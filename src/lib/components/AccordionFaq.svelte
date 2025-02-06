<script>
    // Import d'image
    import arrow from "../../assets/pictures/fleche/arrow.webp"

    const questions = [
        // Contenu sous forme de liste
        {
            title: 'Pourquoi faire appel à un <strong>Expert en Automobiles</strong> ?',
            content: [
                'L’<strong>Expertise automobile</strong> répond à plusieurs besoins techniques et pratiques :',
                {
                    type: 'list',
                    items: [
                        "Évaluation des dommages et des réparations : L’expert identifie la nature des dommages, leur mode de réparation approprié et conforme aux règles de sécurité.",
                        "Recherche des causes et des origines des sinistres ou dysfonctionnements : Cela peut inclure l’analyse d’un défaut de <strong>conformité</strong>, une <strong>malfaçon</strong>, ou encore un <strong>litige</strong> dans le cadre d’une <strong>vente</strong> ou d’un achat.",
                        "Estimation de la valeur des véhicules : L’expert évalue la valeur de tout type de véhicule, qu’il s’agisse de véhicules particuliers, de collection, ou utilitaires.",
                        "Évaluation de la sécurité des véhicules : Garantir que les véhicules respectent les normes de sécurité en vigueur et sont aptes à circuler sur les routes.",
                    ]
                }
            ]
        },
        {
            title: 'Je viens d’acquérir un véhicule occasion et il est affecté d’avaries que doit-je faire(valable vendeur particulier et professionnel) ? ',
            content: [
                'Dans un premier temps, il est essentiel d’informer le vendeur par courrier recommandé de mise en demeure, en joignant si possible le devis de remise en état. Cette démarche formalise les échanges et constitue une étape indispensable pour protéger vos droits en cas de <strong>litige</strong> ultérieur.',
                'Il est également impératif de ne procéder à aucun démontage du véhicule ni à l’effacement des défauts électroniques enregistrés dans les calculateurs du véhicule. Ces mesures conservatoires permettent de préserver les preuves nécessaires à une analyse technique approfondie.',
                'En parallèle, il est indispensable de mandater un <strong>Expert en Automobiles</strong> pour :',
                {
                    type: 'list',
                    items: [
                        "Déterminer l’origine et les causes des avaries, qu’il s’agisse d’un défaut mécanique, électronique ou structurel et de déterminer la date d’apparition de ces désordre avec les moyens techniques en sa possession ainsi que d’établir l'impact de ces avaries sur l’usage du véhicule.",
                        "Identifier si la présence de <strong>vices cachés</strong>, de défaut de <strong>conformité</strong> sont présents sur le véhicule, tels que des dysfonctionnements connus mais non signalés par le vendeur.",
                        "Évaluer si le vendeur a commis un <strong>défaut d’information</strong> ou de conseil lors de la transaction, par exemple en omettant de mentionner :",
                        {
                            type: 'subList',
                            items: [
                                'Des réparations antérieures importantes.',
                                'L’historique complet du véhicule (accidenté, kilométrage <strong>falsifié</strong>, entretien).',
                                'Des problèmes techniques susceptibles d’affecter la sécurité ou la valeur du véhicule.'
                            ]
                        }
                    ]
                },
                'L’<strong>Expertise automobile</strong> permettra également d’évaluer la <strong>conformité</strong> du véhicule par rapport à ce qui était stipulé lors de la <strong>vente</strong> (description dans l’annonce, verbal ou écrit) et d’établir les responsabilités en cas de manquements.',
                'Ces actions combinées vous offriront une base solide pour faire valoir vos droits, que ce soit dans un cadre amiable ou judiciaire.',
            ]
        },
        {
            title: 'Après une prestation de réparation sur mon véhicule, j’ai remarqué qu’il présentait la même <strong>panne</strong> qu’auparavant ou une autre <strong>panne</strong> apparait. Que dois-je faire ?',
            content: [
                'Premièrement, il est nécessaire d’informer le <strong>réparateur</strong> par courrier recommandé de mise en demeure, en incluant si possible le devis de remise en état. Cette étape permet de formaliser les échanges et de protéger vos droits en cas de contentieux ultérieur :',
                'Il est également impératif de ne procéder à aucun démontage du véhicule ni d’effacement des défauts électroniques dans les calculateurs du véhicule, et ce, par mesure conservatoire. En parallèle de ces actions, il est impératif de mandater un <strong>Expert en Automobiles</strong> pour :',
                {
                    type: 'list',
                    items: [
                        "Déterminer l’origine et les causes des avaries afin d’identifier les responsabilités.",
                        "Vérifier si une <strong>mauvaise réparation</strong> a engendré des dommages supplémentaires sur votre véhicule (<strong>malfaçon</strong> ou non-façon).",
                        "Évaluer si le <strong>réparateur</strong> a commis un <strong>défaut de conseil</strong>, par exemple en omettant de signaler des réparations nécessaires, des risques liés aux travaux effectués ou des recommandations techniques essentielles pour le bon entretien du véhicule.",
                    ]
                }
            ]
        },
        // Contenu sous forme de paragraphe
        {
            title: "Mon véhicule est atteint d’un défaut constructeur. Que dois je faire ?",
            content: [
                "En l’absence de prise en charge du constructeur de votre désordre, il est tout d’abord nécessaire d’informer par courrier recommandé de mise en demeure, en incluant si possible le devis de remise en état. Cette étape permet de formaliser les échanges et de protéger vos droits en cas de contentieux ultérieur.",
                "En parallèle, il est indispensable de mandater un <strong>Expert en Automobiles</strong> pour analyser le schéma d’entretien du véhicule et de déterminer l’origine et les causes des avaries afin d’identifier la responsabilité du constructeur automobile.",
                "En règle générale aucun lien contractuel direct ne lie le constructeur et le constructeur dans la majeure partie des cas le vendeur du véhicule doit également être appeler à la cause. "
            ]
        },
        {
            title: 'Mon véhicule est classé épave (VEI - Véhicule Économiquement Irréparable), et la valeur d’indemnisation proposée par mon assureur ne correspond pas à la VRADE (Valeur de Remplacement à Dire d’Expert) réelle de mon véhicule :',
            content: [
                {
                    type: 'list',
                    items: [
                        "Première étape : Informez par courrier recommandé le cabinet d’expertise et votre assureur de votre désaccord. Dans ce courrier, expliquez clairement pourquoi vous contestez la valeur fixée et demandez une révision de la VRADE.",
                        "En cas de refus : Si l’expert et votre assureur maintiennent leur position, vous devrez faire appel à un <strong>Expert en Automobiles</strong> indépendant. Cet expert pourra procéder à une évaluation contradictoire avec l’expert initial pour déterminer la juste valeur de votre véhicule.",
                        "Option alternative : Vous pouvez également mandater un expert à titre unilatéral pour obtenir un avis éclairé avant d’entamer d’autres démarches plus longues et coûteuses.",
                    ]
                },
                'Nota important :',
                'Si vous contestez la VRADE après avoir signé les papiers de cession du véhicule, il est possible que l’accès au véhicule soit impossible. Cela limiterait alors la capacité d’évaluer précisément son état et pourrait affaiblir votre position dans le débat concernant sa valeur.',
            ]
        },
        {
            title: "Mon assureur me demande de faire établir une valeur agréée pour fixer la valeur de mon véhicule en cas de sinistre. Que dois-je faire ?",
            content: "Il est nécessaire de faire appel à un <strong>Expert en Automobiles</strong> afin d’évaluer précisément la valeur de votre véhicule. Cette expertise permettra de déterminer une valeur agréée qui sera contractuellement reconnue par votre assureur, garantissant ainsi une indemnisation adaptée en cas de sinistre (vol, mise à l’épave ect…).",
        },
        {
            title: 'J’ai vendu un véhicule d’occasion en tant que particulier, et l’acquéreur m’envoie un courrier de convocation à une expertise contradictoire ou une assignation judiciaire. Que faire ?',
            content: [
                'En phase amiable, il est impératif de faire appel à un <strong>Expert en Automobiles</strong> afin d’être représenté techniquement de la meilleure manière possible. En effet, chaque détail compte dans ce type de <strong>litige</strong>, où il est souvent nécessaire de :',
                {
                    type: 'list',
                    items: [
                        "Dater l’apparition des défauts, afin de déterminer s’ils étaient présents avant la vente.",
                        "Qualifier l’importance du dommage et son évolution dans le temps, afin d’apporter des éléments objectifs à l’analyse du véhicule.",
                    ]
                },
                'L’Expert en Automobiles possède également des connaissances juridiques permettant d’orienter le dossier. Toutefois, en l’absence d’accord entre les parties, il est essentiel de faire analyser votre dossier par un juriste ou un avocat spécialisé en droit automobile. En cas de désaccord persistant, la partie en demande (l\'acquéreur) peut vous assigner et une expertise judiciaire sera ordonnée.',
                'En phase judiciaire, un avocat sera indispensable pour assurer votre défense et faire valoir vos droits, tandis qu’un <strong>Expert en Automobiles</strong> sera essentiel pour accompagner l’expert judiciaire sur des points techniques clés liés à l’état du véhicule.',
            ]
        },
        {
            title: 'J’ai vendu un véhicule d’occasion en tant que professionnel, et l’acquéreur m’envoie une convocation à une expertise contradictoire ou une assignation judiciaire. Que faire ?',
            content: [
                'En phase amiable, il est impératif de faire appel à un <strong>Expert en Automobiles</strong> afin d’être représenté techniquementde la meilleure manière possible. En effet, chaque détail compte dans ce type de <strong>litige</strong>, où il est souvent nécessaire de :',
                {
                    type: 'list',
                    items: [
                        "Dater l’apparition des défauts, afin de déterminer s’ils étaient présents avant ou après la vente.",
                        "Qualifier l’importance du dommage et son évolution dans le temps, afin d’apporter des éléments techniques objectifs.",
                        "Évaluer si le véhicule correspondait aux engagements de vente, notamment en lien avec son état général, son descriptif, et les obligations du vendeur professionnel.",
                    ]
                },
                'L’Expert en Automobiles pourra ainsi examiner des points clés tels que :',
                {
                    type: 'list',
                    items: [
                        "La présence d’éventuels défauts majeurs et leur influence sur l’usage du véhicule.",
                        "L’adéquation du véhicule vendu avec ce qui était annoncé, pouvant concerner la <strong>garantie légale de conformité</strong> ou l’obligation de délivrance conforme.",
                        "Les éventuelles réparations ou modifications effectuées avant la <strong>vente</strong> et leur impact sur l’état du véhicule.",
                    ]
                },
                'L’Expert en Automobiles possède des connaissances juridiques lui permettant d’orienter techniquement le dossier. Toutefois, en cas de désaccord persistant, il est essentiel de faire analyser votre dossier par un juriste ou un avocat spécialisé en droit automobile.',
                "Si l’acquéreur (partie en demande) maintient sa position, il peut vous assigner en justice, et une expertise judiciaire pourra être ordonnée pour trancher sur les aspects techniques du <strong>litige</strong>.",
                "En phase judiciaire, un avocat sera indispensable pour assurer votre défense et faire valoir vos droits, tandis qu’un <strong>Expert en Automobiles</strong> sera essentiel pour analyser et éclairer l’expert judiciaire sur des points techniques liés à l’état du véhicule, sa <strong>conformité</strong> à la vente, et d’éventuels défauts préexistants.",
            ]
        },
        {
            title: 'J’ai réparé un véhicule dans mon atelier, et mon client me convoque à une expertise contradictoire ou m’assigne en justice. Que faire ?',
            content: [
                'En phase amiable, il est impératif de faire appel à un <strong>Expert en Automobiles</strong> afin d’être représenté techniquement et d’apporter une analyse détaillée sur les réparations effectuées. Dans ce type de <strong>litige</strong>, il est souvent nécessaire de :',
                {
                    type: 'list',
                    items: [
                        "Vérifier si l’intervention réalisée est conforme aux règles de l’art et aux préconisations du constructeur.",
                        "Déterminer si les défauts signalés sont liés aux réparations effectuées ou à un autre problème indépendant de l’intervention.",
                        "Évaluer si un éventuel <strong>défaut de conseil</strong> du <strong>réparateur</strong> a pu influencer l’état du véhicule ou l’évolution d’une panne.",
                    ]
                },
                'L’Expert en Automobiles pourra analyser les éléments suivants :',
                {
                    type: 'list',
                    items: [
                        "La <strong>conformité</strong> des réparations effectuées par rapport aux normes et aux obligations du <strong>réparateur</strong>.",
                        "La présence d’un éventuel <strong>défaut de conseil</strong> (ex. : omission d’informer le client d’une réparation nécessaire).",
                        "L’existence de <strong>malfaçons</strong> ou d’une absence de réparation attendue (\"non-façon\").",
                    ]
                },
                'L’Expert en Automobiles possède des connaissances techniques et juridiques lui permettant d’orienter techniquementle dossier. Toutefois, en cas de désaccord persistant, il est essentiel de faire analyser votre dossier par un juriste ou un avocat spécialisé en droit automobile.',
                "Si le client (partie en demande) maintient sa position, il peut vous assigner en justice, et une expertise judiciaire pourra être ordonnée pour analyser les aspects techniques du <strong>litige</strong>.",
                "En phase judiciaire, un avocat sera indispensable pour assurer votre défense et faire valoir vos droits, tandis qu’un <strong>Expert en Automobiles</strong> sera essentiel pour accompagner l’expert judiciaire sur des points techniques liés aux réparations effectuées, à leur <strong>conformité</strong> et aux éventuelles conséquences sur le véhicule.",
            ]
        },
        {
            title: "Un cabinet d'expertise en automobiles établit que ma déclaration de sinistre est incohérente avec les dommages observés sur mon véhicule. Que dois-je faire ?",
            content: [
                'Si l’incohérence provient d’une imprécision majeure dans la déclaration du sinistre (vol, incendie, choc en stationnement ou choc avec un tiers), qu’elle soit volontaire ou involontaire, il est fortement recommandé de ne pas persister dans une version erronée.',
                "En revanche, si votre déclaration est sincère et véritable, il est essentiel de faire appel à un <strong>Expert en Automobiles</strong> indépendant pour réaliser une expertise contradictoire (contre-expertise).",
                {
                    type: 'list',
                    items: [
                        "Si les constatations techniques confirment votre version des faits, l’expert initial pourra être amené à réviser sa position.",
                        "Si l’expert initial maintient son désaccord, une tierce expertise pourra être demandée. Celle-ci sera menée par un troisième expert, qui aura pour mission de trancher définitivement le différend.",
                    ]
                }
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
                <h3>{@html question.title}</h3>
            </div>

            <!-- @html : Utilisé pour insérer le contenu HTML dynamique dans le DOM. Cela permet de rendre des éléments comme <strong>, <em>, ou tout autre HTML valide dans tes chaînes de texte. -->
            {#if openIndex === index}
                <div id={`panel-${index}`} role="region" class="accordeon-item-ouvert">
                    <!-- Si l'élément est une simple chaîne de caractères, l'affiche dans un paragraphe -->
                    {#if typeof question.content === 'string'}
                        <p>{@html question.content}</p>
                    <!-- Si l'élément est un tableau, on boucle dessus -->
                    {:else if Array.isArray(question.content)}
                        {#each question.content as contentItem}
                            <!-- Si l'élément est une chaîne de caractères, l'affiche dans un paragraphe -->
                            {#if typeof contentItem === 'string'}
                                <p>{@html contentItem}</p>
                            <!-- Si l'élément est une liste, on l'affiche dans une liste non ordonnée -->
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

                ul {
                    list-style-type: disc;
                    padding-left: 1rem;

                    li {
                        padding-top: 0.5rem;
                        list-style-type: inherit;
                    }

                    .subList-wrapper {
                        list-style-type: none; // Supprime la puce du <li> parent contenant la sous-liste
                    }

                    .subList {
                        list-style-type: circle;
                    }
                }
            }
        } 
    }
</style>