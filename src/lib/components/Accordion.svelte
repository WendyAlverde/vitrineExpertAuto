<script>
    export let title = 'FAQ';
    const questions = [
        {
            title: 'Pourquoi faire appel à un expert en automobile ?',
            content: 'L’expertise automobile répond à plusieurs besoins techniques et pratiques : ...'
        },
        {
            title: "Je viens d'acquérir un véhicule d'occasion, il est affecté d'avaries, quels sont mes recours ?",
            content: 'En cas d’accident pour évaluer les dommages subis par votre véhicule ...'
        },
        {
            title: 'Après une prestation de réparations sur mon véhicule, j\'ai remarqué qu\'il présentait la même panne qu\'auparavant.',
            content: 'En cas d’accident pour évaluer les dommages subis par votre véhicule ...'
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


<div class="accordeon">
    {#each questions as question, index}
        <div class="accordeon-item">
            <div class="accordion-header"  role="button" tabindex="0" aria-expanded={openIndex === index ? 'true' : 'false'} aria-controls={`panel-${index}`} on:keydown={(e) => handleKeydown(e, index)} on:click={() => toggleAccordion(index)}>
                <h3>{question.title}</h3>
                <p aria-hidden="true" class="arrow" class:down={openIndex === index}>↓</p>
            </div>
            {#if openIndex === index}
                <div id={`panel-${index}`} role="region" class="accordeon-ouvert">
                    <p>{question.content}</p>
                </div>
            {/if}
        </div>
    {/each}
</div>

<style lang="scss">
    .accordeon {
        border: 0.15rem solid var(--faqLogo);
        border-radius: 0.625rem;
        padding: 0.5rem;
        margin-bottom: 0.5rem;

        .accordion-header {
            cursor: pointer; // Ajoute le curseur pour indiquer que c'est cliquable  
        }

        .arrow {
            transition: transform 0.3s ease; // Ajoute une transition pour l'animation de la flèche  
        }

        .arrow.down {
            transform: rotate(180deg); // Rotation de la flèche quand l'accordéon est ouvert  
        }

        .accordeon-ouvert {
            padding-top: 0.5rem;
        }
    }
</style>