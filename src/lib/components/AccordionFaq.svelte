<script>
    // Import d'image
    import arrow from "../../assets/pictures/fleche/arrow.webp"

    const questions = [
        // Contenu sous forme de liste
        {
            title: "",
            content: [
                '',
                '',
                '',
                {
                    type: 'list',
                    items: [
                        "",
                        "",
                        "",
                        {
                            type: 'subList',
                            items: [
                                '',
                                '',
                                ''
                            ]
                        }
                    ]
                },
                '',
                '',
            ]
        },
        // Contenu sous forme de paragraphe
        {
            title: "",
            content: [
                "",
                "",
                ""
            ]
        },
    ];

    let openIndex = null;

    function toggleAccordion(index, event) {
    let previousIndex = openIndex;
    openIndex = openIndex === index ? null : index;

    // Si l'utilisateur ouvre une nouvelle question, scroller vers elle
    if (openIndex !== null) {
        setTimeout(() => {
            let questionElement = document.getElementById(`panel-${index}`);
            if (questionElement) {
                scrollToQuestion(questionElement);
            }
        }, 200); // Augmentation du délai pour s'assurer que le DOM est bien mis à jour
    }
    }

    function scrollToQuestion(element) {
        let rect = element.getBoundingClientRect();
        let headerHeight = document.querySelector("header")?.offsetHeight || 100; // Définit une valeur par défaut si le header n'est pas trouvé
        let offset = -headerHeight - 70; // Décalage de 20px supplémentaire pour plus d'espace visuel

        // Calcul de la position cible du scroll
        let scrollY = window.scrollY + rect.top + offset;

        // Défilement en douceur avec le bon décalage
        window.scrollTo({
            top: scrollY,
            behavior: "smooth"
        });
    }

    // Accessibilité
    const handleKeydown = (event, index) => {
        if (event.key === 'Enter' || event.key === ' ') {
            toggleAccordion(index);
        } else if (event.key === 'ArrowDown') {
            document.querySelectorAll('.faq')[index + 1]?.focus();
        } else if (event.key === 'ArrowUp') {
            document.querySelectorAll('.faq')[index - 1]?.focus();
        }
    };

</script>

<div class="accordeon">
    {#each questions as question, index}
        <!-- J'ai ajouté l'événement on:click sur cette div afin de permettre de cliquer n'importe où dans l'accordéon pour le fermer.  -->
        <!-- La navigation clavier est prise en charge avec tabindex="0" et on:keydown. -->
        <section class="accordeon-item faq"
                role="button"
                tabindex="0"
                aria-expanded={openIndex === index ? 'true' : 'false'}
                aria-controls={`panel-${index}`}
                on:keydown={(e) => handleKeydown(e, index)}
                on:click={(e) => toggleAccordion(index, e)}>

            <header class="accordeon-item-header">
                <img src={arrow} 
                    class="arrow" 
                    class:down={openIndex === index}
                    alt=""
                    aria-hidden="true"
                >
                <h3 id={`title-${index}`}>{@html question.title}</h3>
            </header>

            <!-- @html : Utilisé pour insérer le contenu HTML dynamique dans le DOM. Cela permet de rendre des éléments comme <strong>, <em>, ou tout autre HTML valide dans tes chaînes de texte. -->
            {#if openIndex === index}
                <section id={`panel-${index}`} 
                    aria-labelledby={`title-${index}`}
                    class="accordeon-item-ouvert">

                    {#if typeof question.content === 'string'}
                        <p>{@html question.content}</p>
                    {:else if Array.isArray(question.content)}
                        {#each question.content as contentItem}
                            {#if typeof contentItem === 'string'}
                                <p>{@html contentItem}</p>
                            {:else if contentItem.type === 'list'}
                                <ul>
                                    {#each contentItem.items as item}
                                        <!-- Si l'élément est une chaîne simple -->
                                        {#if typeof item === 'string'}
                                            <li>{@html item}</li>
                                        <!-- Si l'élément est une sous-liste -->
                                        {:else if item.type === 'subList'}
                                            <li class="subList-wrapper">
                                                <p>{item.title || ''}</p>
                                                <ul class="subList">
                                                    {#each item.items as subItem}
                                                        <li>{@html subItem}</li>
                                                    {/each}
                                                </ul>
                                            </li>
                                        {/if}
                                    {/each}
                                </ul>
                            {/if}
                        {/each}
                    {/if}
                </section>
            {/if}
        </section>
    {/each}
</div>


<style lang="scss">
    .accordeon { 
        &-item {
            border: 0.15rem solid var(--faqLogo);
        } 
    }
</style>