<script>
    import {link} from "svelte-spa-router"
    
    import logoIeta from "../../assets/pictures/logoIeta.png"
</script>

<header>
    <div class="entreprise">
        <img src={logoIeta} alt="Logo I.E.T.A : Innovation, expertise des technologies automobiles">
        <div class="entreprise-name">
            <p class="entreprise-name-titre">Cabinet I.E.T.A</p>
            <p class="entreprise-name-p">Innovation, Expertise des Technologies Automobiles</p>
        </div>
    </div>

    <div class="contact">
        <!-- Invisible pour la partie mobile -->
        <p class="contact-pc">Contactez nous ?</p>
        <p class="contact-pc">Amaury Madani</p>
        <!--  -->
        <div class="contact-row">
            <!-- Invisible pour la partie pc -->
            <a href="/" use:link class="contact-row-form form">Contactez-nous ?</a> <!-- Changer le lien pour amener au formulaire de contact-->
            <!--  -->
            <a class="contact-mobile" href="tel:0123456789">01.23.45.67.89</a> <!-- Changer les numéro de téléphone par le sien-->
        </div>
        <div class="contact-row accueil">
            <a class="contact-mobile" href="mailto:amaury@gmail.com">amaury@gmail.com</a> <!-- Changer l'email par le sien-->
            <a href="/" use:link aria-label="Retour à l'accueil">Accueil</a>
        </div>
    </div>
</header>

<style lang="scss">
    header {
        background: linear-gradient(135deg, #2b2b3d, #41415c);
        display: flex;
        flex-direction: column;
        position: sticky;
        top: 0;
        z-index: 1;

        @media (min-width: 769px) { // Grand écran
            flex-direction: row;
            justify-content: space-between;
            align-items: center;
            padding: 0 1rem;
        }

        .entreprise {
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 0 0.8rem;

            @media (min-width: 515px) and (max-width: 768px) { // Moyen écran
                justify-content: flex-start; 
                padding-left: 1rem;
            }

            @media (min-width: 769px) { // Grand écran
                justify-content: flex-start;
                flex-direction: row;
                align-items: center;
            }

            img {
                width: 7rem;

                @media (min-width: 515px) and (max-width: 768px) { // Moyen écran
                    margin-right: 1rem;
                }

                @media (min-width: 769px) { // Grand écran
                    width: 9rem;
                }
            }

            &-name { 

                @media (min-width: 515px) and (max-width: 768px) { // Moyen écran
                    width: 80%;
                }

                @media (min-width: 769px) { // Grand écran
                    width: 9rem;
                    margin-right: 1rem;
                    width: 80%;
                }

                &-titre {
                    font-weight: bold;
                    font-size: 0.938rem;
                    color: white;
                    letter-spacing: 0.07rem;
                    text-align: center;
                }

                &-p {
                    // font-weight: bold;
                    font-size: 0.7rem;
                    color: white;
                    letter-spacing: 0.03rem;
                    text-align: center;
                }
            }  
        }

        .contact {
            padding: 0 1rem;
            display: flex;
            flex-direction: column;
            gap: 0.5rem;

            @media (min-width: 321px) and (max-width: 514px) { // Petit écran
                flex-direction: row;
                justify-content: space-between;
            }

            @media (min-width: 515px) and (max-width: 768px) { // Moyen écran
                flex-direction: row;
                justify-content: center;
            }

            @media (min-width: 769px) { // Grand écran
                flex-direction: row;
                justify-content: flex-end;
                align-items: center; 
            }
            
            &-pc {
                display: none;
            }

            &-row {
                display: flex;
                justify-content: space-between;
                align-items: center;
                padding: 0.1rem;

                @media (min-width: 321px) and (max-width: 514px) { // Petit écran
                    flex-direction: column;
                    gap: 0.5rem;
                }

                @media (min-width: 515px) and (max-width: 768px) { // Moyen écran
                    white-space: nowrap;
                }

                a {
                    color: white;
                    font-size: 0.8rem;
                    letter-spacing: 0.05rem;

                    @media (min-width: 515px) and (max-width: 768px) { // Moyen écran
                        padding: 0 0.5rem;
                        white-space: nowrap;
                    }

                    @media (min-width: 769px) { // Grand écran
                        padding-left: 0.5rem;
                        white-space: nowrap;
                    }
                }

                .form {
                    color: var(--clickableElement);
                }
            } 
        }
    }
</style>