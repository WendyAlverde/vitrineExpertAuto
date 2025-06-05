<!-- Version anonymisée. Les départements et villes réels du client ont été supprimé. -->

<script>
    import arrow from "../../assets/pictures/fleche/arrow.webp";

    const zones = [
        { dept: "", cities: ["", "", ""] },
        { dept: "", cities: ["", "", ""] },
    ];

    let openIndex = null;

    const toggleAccordion = (index) => {
        openIndex = openIndex === index ? null : index;
    };

    const handleKeydown = (event, index) => {
        if (event.key === 'Enter' || event.key === ' ') {
            toggleAccordion(index);
        } else if (event.key === 'ArrowDown') {
            document.querySelectorAll('.zone-item')[index + 1]?.focus();
        } else if (event.key === 'ArrowUp') {
            document.querySelectorAll('.zone-item')[index - 1]?.focus();
        }
    };
</script>

<section class="zonesIntervention">
    <h2>Zones d'intervention</h2>
    <p>Déplacements ...</p>

    <div class="accordeon">
        {#each zones as zone, index}
            <div class="accordeon-item zone-item" 
                role="button" 
                tabindex="0" 
                aria-expanded={openIndex === index ? 'true' : 'false'} 
                aria-controls={`panel-zone-${index}`} 
                on:keydown={(e) => handleKeydown(e, index)} 
                on:click={() => toggleAccordion(index)}>

                <div class="accordeon-item-header">
                    <img src={arrow} aria-hidden="true" class="arrow" class:down={openIndex === index} alt="">
                    <h3>{@html zone.dept}</h3>
                </div>

                {#if openIndex === index}
                    <div id={`panel-zone-${index}`} role="region" class="accordeon-item-ouvert">
                        <ul>
                            {#each zone.cities as city}
                                <li>{@html city}</li>
                            {/each}
                        </ul>
                    </div>
                {/if}
            </div>
        {/each}
    </div>
</section>

<style lang="scss">
    .zonesIntervention {
        background-color: white;
        border-radius: 0.625rem;
        padding: 1.5rem;

        h2 {
            padding-bottom: 0.8rem;
            text-align: center;
        }

        p {
            margin-bottom: 1rem;
            text-align: center;
        }

        .accordeon {
            &-item {
                border: 0.15rem solid var(--backgroundComponents);
            }

            @media screen and (min-width: 1024px) { // Laptop
                display: grid;
                grid-template-columns: repeat(2, auto); 
                gap: 0.5rem 2.8rem; 
                align-items: start; 
            }

            @media screen and (min-width: 1440px) { // Grand écran
                grid-template-columns: repeat(3, auto); 
                gap: 0.8rem 3.5rem; 
            }
        }  
    }
</style>