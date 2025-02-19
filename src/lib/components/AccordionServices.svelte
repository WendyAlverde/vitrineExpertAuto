<script>
    // Import d'image
    import arrow from "../../assets/pictures/fleche/arrow.webp"

    const services = [
        {
            title: "Litiges après l'achat ou la vente d'un véhicule :",
            content: [
                "Analyse des <strong>vices cachés</strong> ou des <strong>défauts de conformité</strong> affectant le véhicule.",
                "Identification des responsabilités dans un <strong>litige</strong> entre vendeur et acheteur.",
            ]
        },
        {
            title: "Problèmes après une réparation automobile :",
            content: [
                "Vérification des <strong>malfaçons</strong> ou <strong>réparations</strong> non conformes.",
                "Détermination de l’impact technique d’un <strong>défaut de réparation</strong>.",
                "Analyse des conséquences d’un <strong>défaut d’information</strong> du garagiste.",
            ]
        },
        {
            title: "Refus d’indemnisation ou contestation d’un rapport d’expert d’assurance (contre-expertise) :",
            content: [
                "<strong>Contre-expertise</strong> en cas de désaccord avec un rapport d’assurance.",
                "Reconstitution de <strong>sinistres</strong>, recherche des causes d’un incendie ou d’un <strong>vol de véhicule</strong>.",
            ]
        },
        {
            title: "Évaluation de la valeur d’un véhicule :",
            content: [
                "Estimation de la valeur de <strong>véhicules de collection ou de prestige</strong>.",
                "Expertise agréée pour assurer ou vendre un véhicule.",
                "Évaluation pour divorce, succession ou <strong>revente</strong>.",
            ]
        },
        {
            title: "Contestation d’un contrôle technique défaillant :",
            content: "Analyse des <strong>défauts</strong> non détectés lors du contrôle technique."
        },
        {
            title: "Mise en cause du constructeur automobile :",
            content: "Évaluation des <strong>défauts</strong> de fabrication ou <strong>malfaçons</strong> engageant la responsabilité du constructeur."
        },
        {
            title: "Tierce expertise :",
            content: "Intervention pour trancher un désaccord après une <strong>contre-expertise</strong> n’ayant pas abouti."
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
        <!-- Si cela pose problème, vous pouvez déplacer l'événement sur la div située en dessous. -->
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