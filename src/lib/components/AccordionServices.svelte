<script>
    // Import d'image
    import arrow from "../../assets/pictures/fleche/arrow.webp"

    const questions = [
        {
            title: "En cas de litiges... :",
            content: "..."
        },
        {
            title: "Expertise de véhicules... :",
            content: "..."
        },
        {
            title: "Assistance a l'achat d'un véhicule d'occasion... :",
            content: "..."
        }
    ];

    let openIndex = null;

    const toggleAccordion = (index) => {
        openIndex = openIndex === index ? null : index; // Ferme si la même section est cliquée  
    };

    // Accessibilité
    const handleKeydown = (event, index) => {
    if (event.key === 'Enter' || event.key === ' ') {
        toggleAccordion(index);
        }
    };
</script>

<div class="accordeon" >
    {#each questions as question, index}
        <div class="accordeon-item" role="button" tabindex="0" aria-expanded={openIndex === index ? 'true' : 'false'} aria-controls={`panel-${index}`} on:keydown={(e) => handleKeydown(e, index)} on:click={() => toggleAccordion(index)}>
            <div class="accordeon-item-header"> 
                <img src={arrow} aria-hidden="true" class="arrow" class:down={openIndex === index} alt="">
                <h3>{question.title}</h3>
            </div>

            {#if openIndex === index}
                <div id={`panel-${index}`} role="region" class="accordeon-item-ouvert">
                    {#each question.content as contentItem}
                        {#if typeof contentItem === 'string'}
                            <p>{contentItem}</p>
                        {:else if contentItem.type === 'list'}
                            <ul>
                                {#each contentItem.items as item}
                                    <li>{@html item}</li>
                                {/each}
                            </ul>
                        {/if}
                    {/each}
                </div>
            {/if}
        </div>
    {/each}
</div>

<style lang="scss">
    .accordeon {
        cursor: pointer; 

        &-item {
            border: 0.15rem solid var(--backgroundComponents);
            border-radius: 0.625rem;
            padding: 0.5rem;
            margin-bottom: 0.5rem; 

            &-header {
                display: flex;
                align-items: center;

                .arrow {
                    width: 1rem;
                    transition: transform 0.3s ease;
                    transform: rotate(270deg);

                    @media screen and (min-width: 768px) {
                        width: 1.5rem;
                    }

                    &.down {
                        transform: rotate(360deg); 
                    }
                }  
                
                h3 {
                    padding-left: 0.5rem;

                    @media screen and (min-width: 768px) {
                        padding-left: 1.5rem;
                    }
                }
            }

            &-ouvert {
                padding: 0.5rem 0.2rem;

                @media screen and (min-width: 768px) {
                    padding: 0.8rem;
                }

                // p {

                // }

                ul {
                    list-style-type: disc;
                    padding-left: 1rem;

                    li {
                        padding-top: 0.5rem;
                        list-style-type: inherit;
                    }
                }
            }
        } 

        // améliore la visibilité lors du focus clavier
        .accordeon-item:focus {
            outline: 2px solid var(--form);
            outline-offset: 4px;
        }
    }
</style>