<main>
    <h1>Mentions légales</h1>

    <!-- Informations légales -->
    <section>
        <h2>1. Informations légales</h2>
        <ul>
            <li><em>Dénomination sociale :</em> IETA : Innovation, Expertise des Technologies Automobiles</li>
            <li><em>Forme juridique :</em> SARL</li>
            <li><em>Montant du capital social :</em> 1000€</li>
            <li><em>Adresse du siège social :</em> 145 Rue Lapérouse, 13600 LA CIOTAT</li>
            <li><em>Contact :</em>
                <ul>
                    <li>Email : <a class="contact-mail" href="mailto:cabinet.ieta@outlook.fr" target="_blank" rel="noopener noreferrer" aria-label="Ouverture d'une nouvelle page sur votre application mail">cabinet.ieta@outlook.fr</a></li>
                    <li>Téléphone : <a class="contact-tel" href="tel:0628406288">06 28 40 62 88</a></li>
                </ul>
            </li>
            <li><em>Numéro RCS / RM :</em> ***</li>
            <li><em>Hébergeur du site :</em>
                <ul>
                    <li>Nom : Vercel</li>
                    <li>Raison sociale : Vercel Inc.</li>
                    <li>Adresse : 440 N Barranca Avenue #4133, Covina, CA 91723, United States</li>
                </ul>
            </li>
            <li><em>Responsable de la publication :</em> Amaury Madani</li>
            <li><em>Responsable de la rédaction :</em> Amaury Madani</li>
        </ul>
    </section>

    <!-- Utilisation des cookies -->
    <section>
        <h2>2. Utilisation des cookies</h2>
        <p>Un formulaire de contact est utilisé sur ce site. Ce formulaire <em>n’utilise pas de cookies</em> pour son fonctionnement. Aucun cookie de suivi ou de statistiques n’est collecté via cette fonctionnalité.</p>
    </section>

    <!-- Protection des données personnelles (RGPD) -->
    <section>
        <h2>3. Protection des données personnelles (RGPD)</h2>
        <p>Le site respecte le RGPD (Règlement Général sur la Protection des Données) en vigueur depuis 2018. Les données personnelles collectées via le formulaire de contact (nom, emplacement, téléphone, email) sont traitées dans le cadre suivant :</p>
        <ul>
            <li><em>Responsable du traitement des données :</em> IETA, représentée par Amaury Madani</li>
            <li><em>Finalité du traitement :</em> Les informations recueillies permettent de répondre aux demandes effectuées via le formulaire de contact.</li>
            <li><em>Base légale justifiant le traitement :</em> Consentement explicite donné par l’utilisateur lors de la soumission du formulaire.</li>
            <li><em>Caractère obligatoire ou facultatif :</em> Les champs du formulaire marqués comme obligatoires doivent être remplis pour envoyer une demande.</li>
            <li><em>Personnes ayant accès aux données collectées :</em> Amaury Madani</li>
            <li><em>Durée de conservation :</em> D'après les recommandations de la CNIL en France, les données sont conservées jusqu'à 3 ans après le dernier contact. 
                Si la demande a été traité et qu'aucun suivi n'est nécessaire, les données seront supprimées. 
                Les utilisateurs peuvent demander à tout moment la suppression de leurs données.</li>
            <li><em>Droits des utilisateurs :</em>
                <ul>
                    <li>Droit d’accès à leurs données.</li>
                    <li>Droit de rectification ou de suppression de leurs données.</li>
                    <li>Droit de refuser le traitement de leurs données.</li>
                    <li>Droit de portabilité des données sur demande.</li>
                    <li>Possibilité de déposer plainte auprès de la CNIL.</li>
                </ul>
            </li>
        </ul>
        <p>Pour toute question concernant vos données personnelles ou pour exercer vos droits, vous pouvez nous contacter à l’adresse suivante : <a class="contact-mail" href="mailto:cabinet.ieta@outlook.fr" target="_blank" rel="noopener noreferrer">cabinet.ieta@outlook.fr</a>.</p>
    </section>
</main>

<style lang="scss">

    main {
        max-width: 1000px;
        margin: 1rem;
        padding: 1.5rem;
        background-color: #fff;
        border-radius: 0.625rem;
        box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);

        @media (min-width: 1024px) {
            margin: 2rem auto;
        }

        h1 {
            text-align: center;
        }

        h2 {
            margin-top: 2rem;
            border-bottom: 2px solid var(--text);
            padding-bottom: 0.5rem;
        }

        .contact-mail {
            color: var(--text);
        }

        .contact-tel {
            color: var(--text);
        }

        ul {
            padding-left: 0;
            list-style-type: none;

            li {
                margin: 1rem 0;

                em {
                    font-weight: bold;
                }

                ul {
                    list-style-type: disc;
                }
            }
        }

        p {
            line-height: 1.6;
            margin: 1rem 0;

            a {
                color: var(--text);
                text-decoration: none;
                font-weight: bold;

                &:hover {
                    text-decoration: underline;
                }
            }
        }
    }
</style>