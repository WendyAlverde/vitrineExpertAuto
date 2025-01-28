<script>
    // Import Svelte
    import {onMount} from 'svelte';

    // Import composants
    import AccordionFaq from '../components/AccordionFaq.svelte';
    import AccordionServices from '../components/AccordionServices.svelte';

    // Import images
    import logoBerline from "../../assets/pictures/véhicules/berline.webp";
    import logoTruck from "../../assets/pictures/véhicules/camion.webp";
    import logoPorsche from "../../assets/pictures/véhicules/porsche.webp";
    import logoMoto from "../../assets/pictures/véhicules/moto.webp";
    import logoTractor from "../../assets/pictures/véhicules/tracteur.webp";
    import logoCollection from "../../assets/pictures/véhicules/collection.webp";
    import logoJustice from "../../assets/pictures/logosAmaury/justice.webp"

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
        // vérifie la validité d'une adresse email en respectant les règles suivantes :
        // - La partie avant le @ peut contenir des lettres, chiffres et certains caractères spéciaux (., _, %, +, -).
        // - Un seul @ est autorisé, suivi par le nom de domaine (lettres, chiffres, tirets, et points).
        // - L'email doit se terminer par un TLD valide (ex. .com, .fr) contenant au moins 2 lettres.
        const emailRegex = /^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/;
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
            <h1>Amaury Madani, Expert Automobile</h1>
            <p>Fort de plusieurs années d’expérience, nous mettons notre savoir-faire au service des <strong>automobilistes</strong> et de leur mobilité avec une approche à la fois humaine et professionnelle.<br><br> Passionnés par l’<strong>automobile</strong> et animés par une volonté d’offrir un accompagnement personnalisé, nous nous engageons à analyser chaque situation avec rigueur et transparence. Grâce à une <strong>expertise</strong> technique pointue, nous intervenons dans des domaines variés tels que les <strong>litiges</strong>, les évaluations de dommages ou encore les conseils pour l’achat et la vente de véhicules.<br><br>Attentif aux besoins de ses clients, Amaury Madani privilégie toujours un dialogue clair et constructif, afin d’apporter des solutions adaptées et de garantir leur satisfaction. Confier votre <strong>véhicule</strong> à Amaury Madani, c’est faire le choix d’un Expert à l’écoute, pour qui chaque détail compte.</p>
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
        <AccordionServices />
    </section>
    
    <section class="logoVehicules">
        <img src={logoBerline} alt="Berline">
        <img src={logoCollection} alt="Voiture de collection">
        <img src={logoTruck} alt="Camion">
        <img src={logoPorsche} alt="Voiture de sport">
        <img src={logoMoto} alt="Deux roues motorisés">
        <img src={logoTractor} alt="Véhicule agricole">
        <img src={logoJustice} alt="Juridique">
    </section>
    
    <section class="faq">
        <h2>Foire aux Questions</h2>
        <AccordionFaq />
    </section>
    
    <section id="contact-form" class="formulaire">
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

        scroll-margin-top: 5rem;

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
        }

        .logoVehicules {
            margin-bottom: 1rem;
            

            img {
                width: 18rem;
                max-width: 5rem;
                
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
        }

        #contact-form {
            scroll-margin-top: 6rem;
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
                    display: flex;
                    flex-direction: column;
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