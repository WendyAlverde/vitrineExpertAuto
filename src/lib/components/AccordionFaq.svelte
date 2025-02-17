<script>
    // Import d'image
    import arrow from "../../assets/pictures/fleche/arrow.webp"

    const questions = [
        // Contenu sous forme de liste
        {
            title: 'Pourquoi faire appel à un expert en automobiles ?',
            content: [
                'L’<strong>expertise automobile</strong> répond à plusieurs besoins techniques et pratiques :',
                {
                    type: 'list',
                    items: [
                        "Évaluation des <strong>dommages</strong> et des <strong>réparations</strong> : <br >L’expert identifie la nature des dommages, leur mode de <strong>réparations</strong> approprié et conforme aux règles de <strong>sécurité</strong>.",
                        "Recherche des causes et des origines des <strong>sinistres</strong> ou dysfonctionnements : <br >Cela peut inclure l’analyse d’un <strong>défaut de conformité</strong>, une <strong>malfaçon</strong> (<strong>mauvaise réparation</strong>), ou encore un <strong>litige</strong> dans le cadre d’une <strong>vente</strong> (<strong>vice caché</strong>, <strong>garantie légale de conformité</strong>), ou d’un <strong>achat</strong>, ect ...",
                        "Estimation de la <strong>valeur</strong> des véhicules : <br >L’expert évalue la valeur de tout type de véhicule, qu’il s’agisse de véhicules particuliers, de collection, ou utilitaires.",
                        "Évaluation de la <strong>sécurité</strong> des véhicules : <br >Garantir que les véhicules respectent les normes de <strong>sécurité</strong> en vigueur et sont aptes à circuler sur les routes.",
                    ]
                }
            ]
        },
        {
            title: "Je viens d’acquérir un véhicule d'occasion et il est affecté d’avaries que dois-je faire (valable vendeur particulier et professionnel) ?",
            content: [
                'Dans un premier temps, il est essentiel d’informer le vendeur par courrier recommandé de mise en demeure, en joignant si possible le devis de remise en état. Cette démarche formalise les échanges et constitue une étape indispensable pour protéger vos droits en cas de <strong>litige</strong> ultérieur.',
                'Il est également impératif de ne procéder à aucun démontage du <strong>véhicule</strong> ni à l’effacement des <strong>défauts</strong> électroniques enregistrés dans les calculateurs du véhicule. Ces mesures conservatoires permettent de préserver les preuves nécessaires à une analyse technique approfondie.',
                'En parallèle, il est indispensable de mandater un <strong>expert en automobiles</strong> pour :',
                {
                    type: 'list',
                    items: [
                        "Déterminer l’origine et les causes des avaries, qu’il s’agisse d’un <strong>défaut</strong> mécanique, électronique ou structurel et de déterminer la date d’apparition de ces désordres avec les moyens techniques en sa possession ainsi que d’établir l'impact de ces avaries sur l’usage du <strong>véhicule</strong>.",
                        "Identifier si la présence de <strong>vices cachés</strong>, de <strong>défaut de conformité</strong> sont présents sur l' <strong>automobile</strong>, tels que des dysfonctionnements connus mais non signalés par le vendeur.",
                        "Évaluer si le vendeur a commis un <strong>défaut d’information</strong> ou de conseil lors de la transaction, par exemple en omettant de mentionner :",
                        {
                            type: 'subList',
                            items: [
                                'Des <strong>réparations</strong> antérieures importantes.',
                                'L’historique complet du <strong>véhicule</strong> (accidenté, kilométrage falsifié, entretien).',
                                'Des problèmes techniques susceptibles d’affecter la <strong>sécurité</strong> ou la <strong>valeur</strong> du véhicule.'
                            ]
                        }
                    ]
                },
                'L’<strong>expertise automobile</strong> permettra également d’évaluer la <strong>conformité</strong> du <strong>véhicule</strong> par rapport à ce qui était stipulé lors de la <strong>vente</strong> (description dans l’annonce, verbal ou écrit) et d’établir les responsabilités en cas de manquements.',
                'Ces actions combinées vous offriront une base solide pour faire valoir vos droits, que ce soit dans un cadre amiable ou judiciaire.',
            ]
        },
        {
            title: 'Après une prestation de <strong>réparation</strong> sur mon véhicule, j’ai remarqué qu’il présentait la même panne qu’auparavant ou une autre panne apparait. Que dois-je faire ?',
            content: [
                'Premièrement, il est nécessaire d’informer le <strong>réparateur</strong> par courrier recommandé de mise en demeure, en incluant si possible le devis de remise en état. Cette étape permet de formaliser les échanges et de protéger vos droits en cas de contentieux ultérieur.',
                'Il est également impératif de ne procéder à aucun démontage du <strong>véhicule</strong> ni d’effacement des <strong>défauts</strong> électroniques dans les calculateurs du véhicule, et ce, par mesure conservatoire. En parallèle de ces actions, il est impératif de mandater un <strong>expert en automobiles</strong> pour :',
                {
                    type: 'list',
                    items: [
                        "Déterminer l’origine et les causes des avaries afin d’identifier les responsabilités.",
                        "Vérifier si une <strong>mauvaise réparation</strong> a engendré des <strong>dommages</strong> supplémentaires sur votre véhicule (<strong>malfaçon</strong> ou non-façon).",
                        "Évaluer si le <strong>réparateur</strong> a commis un <strong>défaut de conseil</strong>, par exemple en omettant de signaler des <strong>réparations</strong> nécessaires, des risques liés aux travaux effectués ou des recommandations techniques essentielles pour le bon entretien du <strong>véhicule</strong>.",
                    ]
                }
            ]
        },
        // Contenu sous forme de paragraphe
        {
            title: "Mon véhicule est atteint d’un défaut constructeur. Que dois-je faire ?",
            content: [
                "En l’absence de prise en charge du constructeur de votre désordre, il est tout d’abord nécessaire d’informer par courrier recommandé de mise en demeure, en incluant si possible le devis de remise en état. Cette étape permet de formaliser les échanges et de protéger vos droits en cas de contentieux ultérieur.",
                "En parallèle, il est indispensable de mandater un <strong>expert en automobiles</strong> pour analyser le schéma d’entretien du <strong>véhicule</strong> et de déterminer l’origine et les causes des avaries afin d’identifier la responsabilité du constructeur automobile.",
                "En règle générale, aucun lien contractuel direct ne lie l'acheteur et le constructeur dans la majeure partie des cas le vendeur du <strong>véhicule</strong> doit également être appeler à la cause (<strong>vice caché</strong> ou <strong>défaut de conformité</strong>). "
            ]
        },
        {
            title: 'Mon véhicule est classé épave (VEI - véhicule Économiquement Irréparable), et la valeur d’indemnisation proposée par mon assureur ne correspond pas à la VRADE (Valeur de Remplacement à Dire d’Expert) réelle de mon véhicule :',
            content: [
                {
                    type: 'list',
                    items: [
                        "Première étape : <br > Informez par courrier recommandé le cabinet d’expertise et votre assureur de votre désaccord. Dans ce courrier, expliquez clairement pourquoi vous contestez la <strong>valeur</strong> fixée et demandez une révision de la VRADE.",
                        "En cas de refus : <br > Si l’expert et votre assureur maintiennent leur position, vous devrez faire appel à un <strong>expert en automobiles</strong> indépendant. Cet expert pourra procéder à une <strong>contre-expertise</strong> avec l’expert initial pour déterminer la juste <strong>valeur</strong> de votre <strong>véhicule</strong>.",
                        "Option alternative : <br > Vous pouvez également mandater un expert à titre unilatéral pour obtenir un avis éclairé avant d’entamer d’autres démarches plus longues et coûteuses comme une <strong>contre-expertise</strong>.",
                    ]
                },
                'Nota important : <br > Si vous contestez la VRADE après avoir signé les papiers de cession du <strong>véhicule</strong>, il est possible que l’accès au véhicule soit impossible. Cela limiterait alors la capacité d’évaluer précisément son état et pourrait affaiblir votre position dans le débat concernant sa <strong>valeur</strong>.',
            ]
        },
        {
            title: "Mon assureur me demande de faire établir une valeur agréée pour fixer la valeur de mon véhicule en cas de sinistre. Que dois-je faire ?",
            content: "Il est nécessaire de faire appel à un <strong>expert en automobiles</strong> afin d’évaluer précisément la valeur de votre <strong>véhicule</strong>. Cette expertise permettra de déterminer une <strong>valeur agréée</strong> qui sera contractuellement reconnue par votre assureur, garantissant ainsi une indemnisation adaptée en cas de <strong>sinistre</strong> (vol, mise à l’épave ect…).",
        },
        {
            title: 'J’ai vendu un véhicule d’occasion en tant que particulier, et l’acquéreur m’envoie un courrier de convocation à une expertise contradictoire ou une assignation judiciaire. Que faire ?',
            content: [
                'En phase amiable, il est impératif de faire appel à un <strong>expert en automobiles</strong> afin d’être représenté techniquement de la meilleure manière possible. En effet, chaque détail compte dans ce type de <strong>litige</strong>, où il est souvent nécessaire de :',
                {
                    type: 'list',
                    items: [
                        "Dater l’apparition des défauts, afin de déterminer s’ils étaient présents avant la vente.",
                        "Qualifier l’importance du <strong>dommage</strong> et son évolution dans le temps, afin d’apporter des éléments objectifs à l’analyse du <strong>véhicule</strong>.",
                    ]
                },
                'L’expert en automobiles possède également des connaissances juridiques permettant d’orienter le dossier. Toutefois, en l’absence d’accord entre les parties, il est essentiel de faire analyser votre dossier par un juriste ou un avocat spécialisé en droit automobile. En cas de désaccord persistant, la partie en demande (l\'acquéreur) peut vous assigner et une expertise judiciaire sera ordonnée.',
                'En phase judiciaire, un avocat sera indispensable pour assurer votre défense et faire valoir vos droits, tandis qu’un <strong>expert en automobiles</strong> sera essentiel pour accompagner l’expert judiciaire sur des points techniques clés liés à l’état du <strong>véhicule</strong>.',
            ]
        },
        {
            title: 'J’ai vendu un véhicule d’occasion en tant que professionnel, et l’acquéreur m’envoie une convocation à une expertise contradictoire ou une assignation judiciaire. Que faire ?',
            content: [
                'En phase amiable, il est impératif de faire appel à un <strong>expert en automobiles</strong> afin d’être représenté techniquement de la meilleure manière possible. En effet, chaque détail compte dans ce type de <strong>litige</strong>, où il est souvent nécessaire de :',
                {
                    type: 'list',
                    items: [
                        "Dater l’apparition des défauts, afin de déterminer s’ils étaient présents avant ou après la vente.",
                        "Qualifier l’importance du <strong>dommage</strong> et son évolution dans le temps, afin d’apporter des éléments techniques objectifs.",
                        "Évaluer si le <strong>véhicule</strong> correspondait aux engagements de vente, notamment en lien avec son état général, son descriptif, et les obligations du vendeur professionnel.",
                    ]
                },
                'L’<strong>expert en automobiles</strong> pourra ainsi examiner des points clés tels que :',
                {
                    type: 'list',
                    items: [
                        "La présence d’éventuels de <strong>défauts</strong> majeurs et leur influence sur l’usage du <strong>véhicule</strong>.",
                        "L’adéquation du véhicule vendu avec ce qui était annoncé, pouvant concerner la <strong>garantie légale de conformité</strong> ou l’obligation de délivrance conforme.",
                        "Les éventuelles <strong>réparations</strong> ou modifications effectuées avant la <strong>vente</strong> et leur impact sur l’état du <strong>véhicule</strong>.",
                    ]
                },
                'L’expert en automobiles possède des connaissances juridiques lui permettant d’orienter techniquement le dossier. Toutefois, en cas de désaccord persistant, il est essentiel de faire analyser votre dossier par un juriste ou un avocat spécialisé en droit automobile.',
                "Si l’acquéreur (partie en demande) maintient sa position, il peut vous assigner en justice, et une expertise judiciaire pourra être ordonnée pour trancher sur les aspects techniques du <strong>litige</strong>.",
                "En phase judiciaire, un avocat sera indispensable pour assurer votre défense et faire valoir vos droits, tandis qu’un <strong>expert en automobiles</strong> sera essentiel pour analyser et éclairer l’expert judiciaire sur des points techniques liés à l’état du <strong>véhicule</strong>, sa <strong>conformité</strong> à la vente, et d’éventuels <strong>défauts</strong> préexistants.",
            ]
        },
        {
            title: 'J’ai réparé un véhicule dans mon atelier, et mon client me convoque à une expertise contradictoire ou m’assigne en justice. Que faire ?',
            content: [
                'En phase amiable, il est impératif de faire appel à un <strong>expert en automobiles</strong> afin d’être représenté techniquement et d’apporter une analyse détaillée sur les <strong>réparations</strong> effectuées. Dans ce type de <strong>litige</strong>, il est souvent nécessaire de :',
                {
                    type: 'list',
                    items: [
                        "Vérifier si l’intervention réalisée est conforme aux règles de l’art et aux préconisations du constructeur.",
                        "Déterminer si les <strong>défauts</strong> signalés sont liés aux <strong>réparations</strong> effectuées ou à un autre problème indépendant de l’intervention.",
                        "Évaluer si un éventuel <strong>défaut de conseil</strong> du <strong>réparateur</strong> a pu influencer l’état du <strong>véhicule</strong> ou l’évolution d’une panne.",
                    ]
                },
                'L’expert en automobiles pourra analyser les éléments suivants :',
                {
                    type: 'list',
                    items: [
                        "La <strong>conformité</strong> des <strong>réparations</strong> effectuées par rapport aux normes et aux obligations du <strong>réparateur</strong>.",
                        "La présence d’un éventuel <strong>défaut de conseil</strong> (ex. : omission d’informer le client d’une <strong>réparations</strong> nécessaire).",
                        "L’existence de <strong>malfaçons</strong> ou d’une absence de <strong>réparations</strong> attendue (\"non-façon\").",
                    ]
                },
                'L’expert en automobiles possède des connaissances techniques et juridiques lui permettant d’orienter techniquement le dossier. Toutefois, en cas de désaccord persistant, il est essentiel de faire analyser votre dossier par un juriste ou un avocat spécialisé en droit automobile.',
                "Si le client (partie en demande) maintient sa position, il peut vous assigner en justice, et une expertise judiciaire pourra être ordonnée pour analyser les aspects techniques du <strong>litige</strong>.",
                "En phase judiciaire, un avocat sera indispensable pour assurer votre défense et faire valoir vos droits, tandis qu’un <strong>expert en automobiles</strong> sera essentiel pour accompagner l’expert judiciaire sur des points techniques liés aux <strong>réparations</strong> effectuées, à leur <strong>conformité</strong> et aux éventuelles conséquences sur le <strong>véhicule</strong>.",
            ]
        },
        {
            title: "Un cabinet d'expertise en automobiles établit que ma déclaration de <strong>sinistre</strong> est incohérente avec les <strong>dommages</strong> observés sur mon véhicule. Que dois-je faire ?",
            content: [
                'Si l’incohérence provient d’une imprécision majeure dans la déclaration du <strong>sinistre</strong> (vol, incendie, choc en stationnement ou choc avec un tiers), qu’elle soit volontaire ou involontaire, il est fortement recommandé de ne pas persister dans une version erronée.',
                "En revanche, si votre déclaration est sincère et véritable, il est essentiel de faire appel à un <strong>expert en automobiles</strong> indépendant pour réaliser une expertise contradictoire (<strong>contre-expertise</strong>).",
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
</script>

<div class="accordeon" >
    {#each questions as question, index}
        <!-- J'ai ajouté l'événement on:click sur cette div afin de permettre de cliquer n'importe où dans l'accordéon pour le fermer.  -->
        <!-- Si cela pose problème, vous pouvez déplacer l'événement sur la div située en dessous. -->
        <!-- La navigation clavier est prise en charge avec tabindex="0" et on:keydown. -->
        <div    class="accordeon-item"
                role="button"
                tabindex="0"
                aria-expanded={openIndex === index ? 'true' : 'false'}
                aria-controls={`panel-${index}`}
                on:keydown={(e) => handleKeydown(e, index)}
                on:click={(e) => toggleAccordion(index, e)}>

            <div class="accordeon-item-header">
                <img src={arrow} aria-hidden="true" class="arrow" class:down={openIndex === index} alt="">
                <h3>{@html question.title}</h3>
            </div>

            <!-- @html : Utilisé pour insérer le contenu HTML dynamique dans le DOM. Cela permet de rendre des éléments comme <strong>, <em>, ou tout autre HTML valide dans tes chaînes de texte. -->
            {#if openIndex === index}
                <div id={`panel-${index}`} role="region" class="accordeon-item-ouvert">
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
                </div>
            {/if}
        </div>
    {/each}
</div>


<style lang="scss">
    .accordeon { 
        &-item {
            border: 0.15rem solid var(--faqLogo);
        } 
    }
</style>