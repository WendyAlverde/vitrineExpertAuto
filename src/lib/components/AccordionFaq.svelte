<script>
    // Import d'image
    import arrow from "../../assets/pictures/fleche/arrow.webp"

    const questions = [
        // Contenu sous forme de liste
        {
            title: 'Pourquoi faire appel à un expert en automobile ?',
            content: [
                'L’expertise automobile répond à plusieurs besoins techniques et pratiques :',
                {
                    type: 'list',
                    items: [
                        "Évaluation des dommages et des réparations : L’expert identifie la nature des dommages, leur mode de réparation approprié et conforme aux règles de sécurité.",
                        "Recherche des causes et des origines des sinistres ou dysfonctionnements : Cela peut inclure l’analyse d’un défaut de conformité, une malfaçon, ou encore un litige dans le cadre d’une vente ou d’un achat.",
                        "Estimation de la valeur des véhicules : L’expert évalue la valeur de tout type de véhicule, qu’il s’agisse de véhicules particuliers, de collection, ou utilitaires.",
                        "Évaluation de la sécurité des véhicules : Garantir que les véhicules respectent les normes de sécurité en vigueur et sont aptes à circuler sur les routes.",
                    ]
                }
            ]
        },
        // Contenu sous forme de paragraphe
        {
            title: "Je viens d'acquérir un véhicule d'occasion, il est affecté d'avaries, quels sont mes recours ?",
            content: "En cas d’accident pour évaluer les dommages subis par votre véhicule ..."
        },
        {
            title: "Après une prestation de réparations sur mon véhicule, j\'ai remarqué qu\'il présentait la même panne qu\'auparavant.",
            content: "En cas d’accident pour évaluer les dommages subis par votre véhicule ..."
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
        <!-- J'ai ajouté l'événement on:click sur cette div afin de permettre de cliquer n'importe où dans l'accordéon pour le fermer.  -->
        <!-- Si cela pose problème, vous pouvez déplacer l'événement sur la div située en dessous. -->
        <!-- La navigation clavier est prise en charge avec tabindex="0" et on:keydown. -->
        <div class="accordeon-item" role="button" tabindex="0" aria-expanded={openIndex === index ? 'true' : 'false'} aria-controls={`panel-${index}`} on:keydown={(e) => handleKeydown(e, index)} on:click={() => toggleAccordion(index)}>
            <div class="accordeon-item-header"> 
                <img src={arrow} aria-hidden="true" class="arrow" class:down={openIndex === index} alt="">
                <h3>{question.title}</h3>
            </div>

            <!-- Affiche le contenu de l'accordéon uniquement si celui-ci est ouvert. -->
            {#if openIndex === index}
                <div id={`panel-${index}`} role="region" class="accordeon-item-ouvert">
                    <!-- Parcourt les éléments du contenu de la question. -->
                    {#each question.content as contentItem}
                    {console.log(contentItem)}
                        <!-- Si l'élément est une simple chaîne de caractères, l'affiche dans un paragraphe. -->
                        {#if typeof contentItem === 'string'}
                            <p>{contentItem}</p>
                        <!-- Si l'élément est une liste, affiche ses éléments dans une liste non ordonnée. -->
                        {:else if contentItem.type === 'list'}
                            <ul>
                                {#each contentItem.items as item}
                                    <!-- Utilisation de '{@html}' pour permettre l'injection de contenu HTML sécurisé. -->
                                    <!-- Si on passes plus tard à un contenu dynamique (API ou base de données), il faudra valider ou nettoyer les données avant de les afficher avec {@html} sinon risque de XSS -->
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
            border: 0.15rem solid var(--faqLogo);
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