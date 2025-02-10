<script>
    // Import Svelte
    import {onMount} from 'svelte';
    import emailjs from "emailjs-com"

    // Import composants
    import AccordionFaq from '../components/AccordionFaq.svelte';
    import AccordionServices from '../components/AccordionServices.svelte';

    // Import images
    import logoBerline from "../../assets/pictures/vehicules/berline.webp";
    import logoTruck from "../../assets/pictures/vehicules/camion.webp";
    import logoPorsche from "../../assets/pictures/vehicules/porsche.webp";
    import logoMoto from "../../assets/pictures/vehicules/moto.webp";
    import logoTractor from "../../assets/pictures/vehicules/tracteur.webp";
    import logoCollection from "../../assets/pictures/vehicules/collection.webp";
    import logoJustice from "../../assets/pictures/logosAmaury/justice.webp";

    // Fonction de scroll vers l'élément cible
    const scrollToAnchor = () => {
        const target = document.getElementById("contactForm");
        if (target) {
            target.scrollIntoView({ behavior: "smooth" });
        }
    };

    // ==================== Formulaire de contact ==================== //
    // Import des variables pour le formulaire
    let nom = "";
    let email = "";
    let tel = "";
    let demande = "information";
    let urgence = "";
    let localisation = "Montpellier";
    let commentaire = "";
    let errorMessage = "";
    let errorMessageForm = '';
    let errorMessageTelMail = '';

     // Fonction pour envoyer le formulaire
    function envoyerFormulaire() {
        
        if (!email && !tel) {
            errorMessageTelMail = "Veuillez entrer au moins un email ou un numéro de téléphone.";
            console.log(errorMessageTelMail);
            return;
        } else {
            errorMessageTelMail = ''; // Si la condition est remplie, on vide le message d'erreur
        }
        
        // Vérification du format du téléphone avant l'envoi
        if (tel && !/^0[1-9](\.[0-9]{2}){4}$/.test(tel)) {
            errorMessage = "Le numéro de téléphone doit être au format 01.02.03.04.05";
            return;
        }

        // Si l'email est renseigné, on vérifie sa validité
        if (email && !/^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/.test(email)) {
            errorMessageMail = "Veuillez entrer une adresse email valide.";
            return;
        } else {
            errorMessageMail = '';  // Réinitialise le message d'erreur pour l'email
        }

        // Informations à envoyer
        let templateParams = {
            to_email: "ptiscarabe2036@msn.com", // Remplacez par votre e-mail
            nom,
            email,
            tel,
            demande,
            urgence,
            localisation,
            commentaire
        };

        // Envoi via EmailJS
        emailjs
            .send(
                "service_wjuacsr",
                "template_4bt7327",
                templateParams,
                "Fd61aLMeIyHeGoWgm"
            )
            .then(
                function (response) {
                    alert("Formulaire envoyé avec succès !");
                    console.log("SUCCESS!", response.status, response.text);
                },
                function (error) {
                    alert("Échec de l'envoi.");
                    console.log("FAILED...", error);
                }
            );
    }

    // Téléphone
    let errorMessageTel = '';

    function formatPhoneNumber(event) {
        let value = event.target.value.replace(/\D/g, ''); // Supprime tout sauf les chiffres
        if (value.length > 10) value = value.slice(0, 10); // Limite à 10 chiffres

        // Applique le format : "01.23.45.67.89"
        value = value.replace(/(\d{2})(?=\d)/g, '$1.');

        // Met à jour l'input via event.target.value (évite les bugs avec bind:value)
        event.target.value = value;
        tel = value; // Met à jour la variable Svelte
    }

    function validatePhone() {
        const phoneRegex = /^0[1-9](\.[0-9]{2}){4}$/;
        errorMessageTel = phoneRegex.test(tel) ? "" : "Le numéro doit être au format 01.02.03.04.05";
    }

    // Email
    let errorMessageMail = '';
    
    function validateEmail() {
        // vérifie la validité d'une adresse email en respectant les règles suivantes :
        // - La partie avant le @ peut contenir des lettres, chiffres et certains caractères spéciaux (., _, %, +, -).
        // - Un seul @ est autorisé, suivi par le nom de domaine (lettres, chiffres, tirets, et points).
        // - L'email doit se terminer par un TLD valide (ex. .com, .fr) contenant au moins 2 lettres.
        if (email && !/^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$/.test(email)) {
            errorMessageMail = "Veuillez entrer une adresse email valide : exemple@gmail.com";
        } else {
            errorMessageMail = '';  // Si l'email est valide ou non renseigné, on efface l'erreur
        }
    }

    // Taille du textarea de commentaire
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

<!-- <img src={logoJustice} alt="Juridique"> -->

<section id="home">
    <section class="presentation">
        <div class="presentation-text">
            <h1>Amaury Madani, Expert Automobile</h1>
            <p><em>Une passion devenue expertise.</em><br >Depuis toujours, l’automobile est l’une de mes passions. Après des études spécialisées et une immersion professionnelle dans le secteur à partir de 2013, j’ai été Expert automobile titré en 2020. <br > Fort de plus de 10 ans d’expérience et d’une passion intacte, j’accompagne aujourd’hui particuliers, professionnels et compagnies d’assurances dans leurs démarches liées à l’expertise technique, la résolution de litiges et l’évaluation de véhicules.</p>
            <p class="question">Pourquoi choisir notre cabinet ?</p>
            <ul>
                <li><em>Une expertise reconnue :</em> Diplômé d’état comme Expert en automobile depuis 2020.</li>
                <li><em>Un accompagnement sur mesure :</em> Une approche humaine et personnalisée pour chaque cas.</li>
                <li><em>Une passion pour la précision :</em> Que ce soit pour des litiges complexes ou l’évaluation de véhicules, chaque détail compte.</li>
            </ul>
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
        <h2>Nos Services, Expert Automobile</h2>
        <AccordionServices />
    </section>
    
    <section class="logoVehicules">
        <img src={logoBerline} alt="Berline">
        <img src={logoCollection} alt="Voiture de collection">
        <img src={logoTruck} alt="Camion">
        <img src={logoPorsche} alt="Voiture de sport">
        <img src={logoMoto} alt="Deux roues motorisés">
        <img src={logoTractor} alt="Véhicule agricole">
    </section>
    
    <section class="faq">
        <h2>Foire aux Questions</h2>
        <AccordionFaq />
    </section>
    
    <section id="contactForm" class="formulaire">
        <h2>Formulaire de contact</h2>
        <form on:submit|preventDefault={envoyerFormulaire}>
            <label for="demande">Quel est votre demande ? <span aria-hidden="true">*</span></label>
            <select name="demande" id="demande" bind:value={demande} required aria-required="true">
                <option value="information">Je souhaite avoir une information</option>
                <option value="Expertise">Expertise véhicule</option>
                <option value="autre">Autre</option>
            </select>
    
            <fieldset>
                <legend>Est-elle urgente ? <span aria-hidden="true">*</span></legend>
                <div class="flexRadio">
                    <div class="radio">
                        <input type="radio" name="urgence" id="oui" bind:group={urgence} value="oui" required>
                        <label for="oui">Oui</label>
                    </div>
                    <div class="radio">
                        <input type="radio" name="urgence" id="non" bind:group={urgence} value="non" required>
                        <label for="non">Non</label>
                    </div>
                </div>
            </fieldset>
    
            <div class="localisation">
                <label for="location">Localisation de votre besoin ? <span aria-hidden="true">*</span></label>
                <select name="localisation" id="localisation" bind:value={localisation} required aria-required="true">
                    <option value="Montpellier">Montpellier</option>
                    <option value="Bouches-du-Rhône">Bouches-du-Rhône</option>
                    <option value="Var">Var</option>
                    <option value="Gard">Gard</option>
                    <option value="Hérault">Hérault</option>
                </select>
            </div>
            
            <div class="nom">
                <label for="nom">Votre nom <span aria-hidden="true">*</span></label>
                <input type="text" name="nom" id="nom" bind:value={nom} required aria-required="true">
            </div>
            
            <div class="tel">
                <label for="tel">Votre numéro de téléphone</label>
                <input type="tel" id="tel" bind:value={tel} on:input={formatPhoneNumber} placeholder="01.02.03.04.05">
                {#if errorMessageTel}
                    <p style="color: #CF1F31; font-size: 0.8rem; padding-bottom: 0.5rem;">{errorMessageTel}</p>
                {/if}
            </div>
            
            <div class="email">
                <label for="email">Votre e-mail</label>
                <input type="email" name="email" id="email" bind:value={email} on:blur={validateEmail} placeholder="example@gmail.com" aria-describedby="email-example">
                {#if errorMessageMail}
                    <p style="color: #CF1F31; font-size: 0.8rem; padding-bottom: 0.5rem;">{errorMessageMail}</p>
                {/if}
            </div>
            
            <div class="commentaire">
                <label for="commentaire">Un commentaire <span aria-hidden="true">*</span></label>
                <textarea name="commentaire" id="commentaire" bind:value={commentaire} bind:this={textarea} on:input={adjustSize} required aria-required="true"></textarea>
            </div>

            {#if errorMessageTelMail}
                <p style="color: #CF1F31; font-size: 0.8rem; padding-bottom: 0.5rem;">{errorMessageTelMail}</p>
            {/if}
            
            <button type="submit" disabled={!!errorMessageForm}>Envoyer</button>
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

                em {
                    font-weight: bold;
                }

                .question {
                    padding: 1.2rem 0 0.8rem;
                    font-weight: bold;
                }

                ul {
                    padding-left: 1.5rem;

                    li {
                        list-style-type: disc;
                    }
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

            h2 {
                padding-bottom: 0.8rem;
                text-align: center;
            }
        }

        .logoVehicules {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;

            img {
                width: 5rem;
                margin: 1rem 0.5rem;

                @media screen and (min-width: 768px) { // Tablette
                    width: 6rem;
                }

                @media screen and (min-width: 1024px) { // Laptop
                    width: 7.5rem;
                    margin: 1rem;
                }

                @media screen and (min-width: 1440px) { // Grand écran
                    width: 9rem;
                    margin: 1rem 2.5rem;
                }
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

        #contactForm {
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

                    @media screen and (min-width: 768px) { // Grand écran
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

                    @media screen and (min-width: 768px) { // Grand écran
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

                    @media screen and (min-width: 768px) { // Grand écran
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
                                @media screen and (min-width: 768px) { // Grand écran
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
                    display: flex;
                    flex-direction: column;

                    @media screen and (min-width: 768px) {
                        width: 50%;
                    }
                }

                .email {
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

                    @media screen and (min-width: 768px) { // Grand écran
                        font-size: 1.25rem;
                    }
                }
            }
        }
    }   
</style>