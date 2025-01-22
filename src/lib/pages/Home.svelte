<script>
    import logoCars from "../../assets/pictures/logoCars.svg"
    import {onMount} from 'svelte';

    // ==================== Formulaire de contact ==================== //
    
    // téléphone
    let tel = ''; // Définition d'une variable tel avec laquelle on fait le lien dans l'input grâce a = bind:value={tel}

    function formatPhoneNumber() {
        let value = tel.replace(/\D/g, ''); // Supprime tout les caractères numériques
        if (value.length > 10) value = value.slice(0, 10); // Limite la longueur du numéro à 10 chiffres
        tel = value.replace(/(\d{2})(?=\d)/g, '$1.'); // Applique le format souhaité à savoir un point tout les deux chiffres
    }

    // email
    let email = '';
    let errorMessage = '';
    
    function validateEmail() {
        const emailRegex = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
        if (!emailRegex.test(email)) {
        errorMessage = "Veuillez entrer une adresse email valide : exemple@gmail.com";
        } else {
        errorMessage = '';
        }
    }

    // Taille du textarea de commentaire
    let commentaire = '';
    let textarea;

    function adjustSize() {
        if (textarea) {
        textarea.style.height = 'auto';
        textarea.style.height = `${textarea.scrollHeight}px`;
        }
    }

    onMount (() => {
        adjustSize();
    });
</script>

<section id="home">
    <section class="presentation">
        <div class="presentation-text">
            <h1>Amaury Madani, expert automobile</h1>
            <p>Fort de plusieurs années d’expérience, je met mon savoir-faire au service des <strong>automobilistes</strong> avec une approche à la fois humaine et professionnelle.<br><br> Passionné par l’<strong>automobile</strong> et animé par une volonté d’offrir un accompagnement personnalisé, je m’engage à analyser chaque situation avec rigueur et transparence. Grâce à une <strong>expertise</strong> technique pointue, il intervient dans des domaines variés tels que les <strong>litiges</strong>, les évaluations de dommages ou encore les conseils pour l’achat et la vente de véhicules.<br><br>Attentif aux besoins de ses clients, Amaury Madani privilégie toujours un dialogue clair et constructif, afin d’apporter des solutions adaptées et de garantir leur satisfaction. Confier votre <strong>véhicule</strong> à Amaury Madani, c’est faire le choix d’un expert à l’écoute, pour qui chaque détail compte.</p>
        </div>
        <div class="presentation-valeurs">
            <h2>Nos Valeurs</h2>
            <ul>
                <li>Impartialité</li>
                <li>Intégrité</li>
                <li>Indépendance</li>
                <li>Excellence</li>
            </ul>
        </div>
    </section>

    <section class="services">
        <h2>Nos Services</h2>
        <ul>
            <li><strong>Assistance technique lors de litige :</strong> <br>opposant des tiers professionnels ou particuliers. <br>Exemple : Suite achat d’un véhicule, mauvaise réparation, contestation d’expertise ect...</li>
            <li><strong>Assistance :</strong> <br>à l’achat d’un véhicule d’occasion.</li>
            <li><strong>Évaluation de véhicules :</strong> <br>de collections de prestiges et de véhicules particuliers.</li>
            <li><strong>Conseils juridiques, audit et accompagnement :</strong> <br>auprès des professionnels de la réparation automobiles.</li>
            <li><strong>Expertise :</strong> <br>à distance via appel vidéo.</li>
            <li><strong>Estimation :</strong> <br> de parc automobile de véhicule de flotte entreprise.</li>
        </ul>
    </section>
    
    <section class="logoVehicules">
        <img src={logoCars} alt="Voiture citadine">
    </section>
    
    <section class="faq">
        <h2>FAQ</h2>
        <div class="accordeon">
            <p aria-hidden="true">↓</p>
            <h3>Pourquoi faire appel à un expert en automobile ?</h3>
            <div class="accordeon-ouvert">
                <p>L’expertise automobile répond à plusieurs besoins techniques et pratiques :</p>
                <ul>
                    <li><em>Évaluation des dommages et des réparations :</em>L’expert identifie la nature des dommages, leur mode de réparation approprié etconforme aux règles de sécurité. </li>
                    <li><em>Recherche des causes et des origines des sinistres ou dysfonctionnements :</em>Cela peut inclure l’analyse d’un défaut de conformité, une malfaçon, ou encore un litige dans le cadre d’une vente ou d’un achat.</li>
                    <li><em>Estimation de la valeur des véhicules :</em>L’expert évalue la valeur de tout type de véhicule, qu’il s’agisse de véhicules particuliers, de collection, ou utilitaires.</li>
                    <li><em>Évaluation de la sécurité des véhicules :</em>Garantir que les véhicules respectent les normes de sécurité en vigueur et sont aptes à circuler sur les routes.</li>
                </ul>
            </div>
        </div>
        <div class="accordeon">
            <p aria-hidden="true">↓</p>
            <h3>Dans quel contexte faire appel à un expert automobile ?</h3>
            <p>En cas d’accident pour évaluer les dommages subis par votre véhicule et déterminer le coût des réparations. Pour vérifier l’état général d’un véhicule ou évaluer la valeur d’un véhicule lors d’un achat en vérifiant qu’il ne présente pas de vices cachés. En cas de litiges ou désaccord ou un soupçon de fraude. </p>
        </div>
        <div class="accordeon">
            <p aria-hidden="true">↓</p>
            <h3>Dans quel contexte faire appel à un expert automobile ?</h3>
            <p>En cas d’accident pour évaluer les dommages subis par votre véhicule et déterminer le coût des réparations. Pour vérifier l’état général d’un véhicule ou évaluer la valeur d’un véhicule lors d’un achat en vérifiant qu’il ne présente pas de vices cachés. En cas de litiges ou désaccord ou un soupçon de fraude. </p>
        </div>
    </section>
    
    <section class="formulaire">
        <h2>Formulaire de contact</h2>
        <form action="" method="post" on:submit|preventDefault={() => validateEmail()}>
            <label for="demande">Quel est votre demande ? <span aria-hidden="true">*</span></label>
            <select name="demande" id="demande" required aria-required="true">
                <option value="information">Je souhaite avoir une information</option>
                <option value="Expertise">Expertise véhicule</option>
                <option value="autre">Autre</option>
            </select>
    
            <fieldset>
                <legend>Est-elle urgente ? <span aria-hidden="true">*</span></legend>
                <div class="flexRadio">
                    <div class="radio">
                        <input type="radio" name="urgence" id="oui" value="oui" required>
                        <label for="oui">Oui</label>
                    </div>
                    <div class="radio">
                        <input type="radio" name="urgence" id="non" value="non" required>
                        <label for="non">Non</label>
                    </div>
                </div>
            </fieldset>
    
            <div class="localisation">
                <label for="location">Localisation de votre besoin ? <span aria-hidden="true">*</span></label>
                <select name="localisation" id="localisation" required aria-required="true">
                    <option value="Montpellier">Montpellier</option>
                    <option value="Bouches-du-Rhône">Bouches-du-Rhône</option>
                    <option value="Var">Var</option>
                    <option value="Gard">Gard</option>
                    <option value="Hérault">Hérault</option>
                </select>
            </div>
            
            <div class="nom">
                <label for="nom">Votre nom <span aria-hidden="true">*</span></label>
                <input type="text" name="nom" id="nom" required aria-required="true">
            </div>
            
            <div class="tel">
                <label for="tel">Votre numéro de téléphone</label>
                <input type="tel" name="tel" id="tel" bind:value={tel} pattern="^0[1-9]( [0-9]{2}){4}$" on:input={formatPhoneNumber} placeholder="01.02.03.04.05" aria-describedby="tel-format">
            </div>
            
            <div class="email">
                <label for="email">Votre e-mail</label>
                <input type="email" name="email" id="email" bind:value={email} on:blur={validateEmail} placeholder="example@gmail.com" aria-describedby="email-example">
                {#if errorMessage}
                    <p style="color: #CF1F31; font-size: 0.8rem; padding-bottom: 0.5rem">{errorMessage}</p>
                {/if}
            </div>
            
            <div class="commentaire">
                <label for="commentaire">Un commentaire <span aria-hidden="true">*</span></label>
                <textarea name="commentaire" id="commentaire" bind:value={commentaire} bind:this={textarea} on:input={adjustSize} required aria-required="true"></textarea>
            </div>
            
            <button type="submit" disabled={!!errorMessage}>Envoyer</button>
        </form>
    </section>
</section>

<style lang="scss">
    #home {
        padding: 1rem;

        @media screen and (min-width: 768px) {
            padding: 2rem 3rem;
        }

        .presentation {

            @media screen and (min-width: 768px) {
                display: flex;
                flex-direction: row-reverse;
                align-items: center;
            }

            &-text {
                background-color: white;
                border-radius: 0.625rem;
                padding: 1rem;
                margin-bottom: 1rem;

                @media screen and (min-width: 768px) {
                    margin-left: 1rem;
                }

                h1 {
                    padding-bottom: 0.5rem;
                }
            }

            &-valeurs {
                background-color: white;
                border-radius: 0.625rem;
                padding: 1rem;
                margin-bottom: 1rem;

                @media screen and (min-width: 768px) {
                    height: 13rem;
                }

                h2 {
                    padding-bottom: 0.8rem;
                    text-align: center;
                }

                ul {
                    display: flex;
                    justify-content: center;
                    flex-wrap: wrap;
                    list-style-type: disc;
                    padding-left: 1rem;

                    @media screen and (min-width: 768px) {
                        flex-direction: column;
                    }


                    li {
                        width: 50%;
                        list-style-type: inherit; 
                    }
                }
            }
        }

        .services {
            background-color: white;
            border-radius: 0.625rem;
            padding: 1rem;
            margin-bottom: 1rem;

            h2 {
                padding-bottom: 0.8rem;
                text-align: center;
            }

            ul {
                display: flex;
                flex-direction: column;
                list-style-type: disc;
                padding-left: 1.1rem;
                // margin: 0 0.5rem;

                li {
                    list-style-type: inherit; 
                    padding-bottom: 0.8rem;
                }
            }
        }

        .logoVehicules {
            margin-bottom: 1rem;

            img {
                width: 18rem;
            }
        }

        .faq {
            background-color: white;
            border-radius: 0.625rem;
            padding: 1rem;
            margin-bottom: 1rem;

            h2 {
                padding-bottom: 0.8rem;
                text-align: center;
            }

            .accordeon {
                border: 0.15rem solid var(--faqLogo);
                border-radius: 0.625rem;
                padding: 0.5rem;
                margin-bottom: 0.5rem;

                p:last-of-type {
                    display: none;
                }
            }
        }

        .formulaire {
            background-color: white;
            border-radius: 0.625rem;
            padding: 1rem;
            margin-bottom: 1rem;
            color: var(--form);

            h2 {
                padding-bottom: 0.8rem;
                text-align: center;
            }

            form {
                display: flex;
                flex-direction: column;

                @media screen and (min-width: 768px) {
                    flex-direction: row;
                    flex-wrap: wrap;
                }

                // générale au formulaire
                label, legend {
                    font-size: 0.813rem;
                    font-weight: bold;

                    @media (min-width: 768px) { // Grand écran
                        font-size: 1.375rem;
                    }

                    span {
                        color: red;
                        font-weight: 200;
                    }
                }

                input {
                    font-family: 'poppins';
                    color: var(--form);
                    border: 0.15rem solid var(--form);
                    border-radius: 0.625rem;
                    padding: 0.5rem;
                    margin: 0.5rem 0 0.8rem;

                    @media (min-width: 768px) { // Grand écran
                        font-size: 1rem;
                    }
                }
                
                // début des balises du form
                select {
                    border: 0.15rem solid var(--form);
                    border-radius: 0.625rem;
                    margin: 0.5rem 0 0.8rem;
                    padding: 0.5rem;
                    width: 100%;
                    color: var(--form);
                    cursor: pointer;

                    @media (min-width: 768px) { // Grand écran
                        font-size: 1rem;
                    }
                }

                fieldset {
                    display: flex;

                    @media screen and (min-width: 768px) {
                        width: 50%;
                    }
                    
                    .flexRadio {
                        display: flex;
                        width: 50%;
                        justify-content: space-between;

                        .radio {
                            display: flex;
                            align-items: center;

                            input[type="radio"] {
                                appearance: none; // Supprimer le style natif du bouton radio
                                width: 0.8rem;
                                height: 0.8rem;
                                border: 0.15rem solid var(--form);
                                border-radius: 1rem;
                                cursor: pointer;
                                margin-right: 0.5rem;

                                &:checked {
                                    background-color: var(--form); // Couleur lorsque sélectionné
                                }
                            } 

                            label {
                                @media (min-width: 768px) { // Grand écran
                                    font-size: 1rem;
                                }
                            }
                        }
                    } 
                }

                .localisation {
                    @media screen and (min-width: 768px) {
                        width: 50%;
                    }
                }

                .nom {
                    #nom {
                        @media screen and (min-width: 768px) {
                            margin-right: 1rem;
                        }
                    }
                }

                .nom, .tel, .email {
                    @media screen and (min-width: 768px) {
                        display: flex;
                        flex-direction: column;
                        width: 50%;
                    }
                }

                .email {
                    display: flex;
                    flex-direction: column;
                    width: 100%;
                    padding-right: 1rem;

                    #email {
                        margin-bottom: 0.4rem;
                    }
                }

                .commentaire {
                    @media screen and (min-width: 768px) {
                        width: 100%;
                    }

                    textarea {
                        resize: none;
                        font-family: 'poppins';
                        color: var(--form);
                        border: 0.15rem solid var(--form);
                        border-radius: 0.625rem;
                        padding: 0.5rem;
                        min-width: 100%;
                        max-width: 100%;
                        margin: 0.5rem 0 0.8rem;
                        min-height: 2rem;
                        overflow: hidden;

                        @media screen and (min-width: 768px) {
                            min-width: 80%;
                            max-width: 100%;
                            display: flex;
                            flex-direction: column;
                            // font-size: 1rem;
                        }
                    }
                }
                
                button {
                    background-color: var(--form);
                    border: none;
                    border-radius: 0.625rem;
                    color: white;
                    cursor: pointer;
                    font-size: 1rem;
                    font-weight: bold;
                    letter-spacing: 0.02rem;
                    padding: 0.5rem;
                    width: 100%;

                    @media (min-width: 768px) { // Grand écran
                        font-size: 1.25rem;
                    }
                }
            }
        }
    }   
</style>