<script>
    // Import d'image
    import arrow from "../../assets/pictures/fleche/arrow.webp"

    const services = [
        {
            title: "",
            content: [
                "",
                "",
            ]
        },
        {
            title: "",
            content: [
                "",
                "",
                "",
            ]
        },
    ];

    let openIndex = null;

    const toggleAccordion = (index) => {
        openIndex = openIndex === index ? null : index; // Ferme si la même section est cliquée  
    };

    // Accessibilité
    const handleKeydown = (event, index) => {
        if (event.key === 'Enter' || event.key === ' ') {
            toggleAccordion(index);
        } else if (event.key === 'ArrowDown') {
            document.querySelectorAll('.service')[index + 1]?.focus();
        } else if (event.key === 'ArrowUp') {
            document.querySelectorAll('.service')[index - 1]?.focus();
        }
    };
</script>

<div class="accordeon" >
    {#each services as service, index}
        <!-- J'ai ajouté l'événement on:click sur cette div afin de permettre de cliquer n'importe où dans l'accordéon pour le fermer.  -->
        <!-- La navigation clavier est prise en charge avec tabindex="0" et on:keydown. -->
        <div class="accordeon-item service" 
            role="button" 
            tabindex="0" 
            aria-expanded={openIndex === index ? 'true' : 'false'} 
            aria-controls={`panel-${index}`} 
            on:keydown={(e) => handleKeydown(e, index)} 
            on:click={() => toggleAccordion(index)}>
            
            <div class="accordeon-item-header">
                <img src={arrow} aria-hidden="true" class="arrow" class:down={openIndex === index} alt="">
                <h3>{@html service.title}</h3>
            </div>

            {#if openIndex === index}
                <div id={`panel-${index}`} role="region" class="accordeon-item-ouvert">
                    <!-- Si l'élément est une simple chaîne de caractères, l'affiche dans un paragraphe -->
                    {#if typeof service.content === 'string'}
                        <p>{@html service.content}</p>
                    <!-- Si l'élément est un tableau, on boucle dessus -->
                    {:else if Array.isArray(service.content)}
                        {#each service.content as contentItem}
                            <!-- Si l'élément est une chaîne de caractères, l'affiche dans un paragraphe -->
                            {#if typeof contentItem === 'string'}
                                <p>{@html contentItem}</p>
                            <!-- Si l'élément est une liste, on l'affiche dans une liste non ordonnée -->
                            {:else if contentItem.type === 'list'}
                                <ul>
                                    {#each contentItem.items as item}
                                        <li>{@html item}</li>
                                    {/each}
                                </ul>
                            {/if}
                        {/each}
                    {/if}
                </div>
            {/if}
        </div>
    {/each}
</div>

<style lang="scss">
    .accordeon {
        &-item {
            border: 0.15rem solid var(--backgroundComponents);
        }
    }
</style>