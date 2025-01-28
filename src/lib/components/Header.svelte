<script>
    import {link} from "svelte-spa-router"
    import { onMount } from 'svelte';
    import logoIeta from "../../assets/pictures/logoIeta.png"

    // ==================== Gère le changement de hauteur du header lors du scroll ==================== //
    let isScrolled = false;    
    

    onMount(() => {
        const handleScroll = () => {
            isScrolled = window.scrollY > 0;
        };
        window.addEventListener("scroll", handleScroll);
        // Nettoyage pour éviter les fuites mémoire
        return () => {
            window.removeEventListener("scroll", handleScroll);
        };
    });

    const scrollToAnchor = (event) => {
        event.preventDefault(); // Empêche le comportement par défaut du navigateur
        const targetId = event.target.getAttribute('href').substring(1); // Récupère l'ID cible (sans le #)
        const targetElement = document.getElementById(targetId);

        if (targetElement) {
            targetElement.scrollIntoView({ behavior: 'smooth' }); // Scroll fluide vers l'élément cible
        }
    };

</script>

<header class="header {isScrolled ? 'scrolled' : ''}">
    <div class="header-content">
        <div class="entreprise">
            <a href="#home" aria-label="Retour à l'accueil"><img src={logoIeta} alt="Logo IETA : Innovation, expertise des technologies automobiles"></a>
            
            <div class="entreprise-name">
                <p class="entreprise-name-titre">Cabinet <em>IETA</em></p>
                <p class="entreprise-name-p">Innovation, Expertise des Technologies Automobiles</p>
            </div>
        </div>
    
        <div class="sticky">
            <div class="contact">
                <div  class="contact-gauche">
                    <a href="#contact-form" class="contact-form form" onclick={scrollToAnchor}>Formulaire Contact</a> <!-- Changer le lien pour amener au formulaire de contact-->
                    <!-- Invisible pour la partie mobile -->
                    <p class="contact-pc">Amaury Madani</p>
                    <!--  -->
                    <a class="contact-mail" href="mailto:amaury@gmail.com">amaury@gmail.com</a> <!-- Changer l'email par le sien-->
                </div>
                <div  class="contact-droite">
                    <a class="contact-tel" href="tel:0123456789">01.23.45.67.89</a> <!-- Changer les numéro de téléphone par le sien-->
                    <a class="accueil-mobile" href="#home" aria-label="Aller sur la page d'accueil">Accueil</a>
                </div>
                
            </div>

            <!-- Partie Laptop -->
            <div class="nav">
                <a class="accueil-tablette" href="#home" aria-label="Aller sur la page d'accueil">Accueil</a>
            </div>
        </div>
    </div>
</header>

<style lang="scss">

    .header {
        position: sticky;
        top: 0; 
        z-index: 1; 
        background: linear-gradient(135deg, #2b2b3d, #41415c);
        height: auto;
        
        &.scrolled {
            height: 6rem; // Header réduit après scroll

            @media (min-width: 768px) { // Tablette
                height: 7rem;
            }

            @media screen and (min-width: 1024px) and (max-width: 1439px) { // Laptop
                height: 7rem;
            }

            @media screen and (min-width: 1440px) { // Laptop
                height: 5.5rem;
            }

            .header-content {
                transform: translateY(-5.5rem); // Décale le contenu vers le haut
                transition: transform 0.6s ease; 

                @media screen and (min-width: 1024px) { // Laptop
                    transform: translateY(-6.2rem); // Décale le contenu vers le haut
                }

                @media screen and (min-width: 1024px) { // Laptop
                    transform: translateY(-6.2rem); // Décale le contenu vers le haut
                }
            }
        }

        .header-content {
            height: auto; // Taille réelle du contenu 
            transition: transform 0.8s ease; 
        }
        
        .entreprise {
            display: flex;
            align-items: center;
            padding: 0 0.5rem;
            position: relative;
            

            a {
                display: block;
                position: absolute;
                top: 0;
                left: 0;

                img {
                    width: 7rem;

                    @media (min-width: 768px) { // Tablette
                        width: 7.5rem;
                    }

                    @media (min-width: 1024px) { // Laptop
                        width: 8rem;
                    }
                }
            }

            &-name { 
                display: flex;
                flex-direction: column;
                align-items: center;
                justify-content: center;
                width: 100%;
                margin-left: 7rem;
                height: 6rem;

                &-titre {
                    font-weight: bold;
                    
                    color: white;
                    letter-spacing: 0.07rem;
                    padding-bottom: 0.2rem;

                    em {
                        letter-spacing: 0.3rem;
                        font-size: 1rem;

                        @media (min-width: 768px) { // Tablette
                            font-size: 1.8rem;
                        }
                    }
                }

                &-p {
                    
                    color: white;
                    letter-spacing: 0.03rem;
                    text-align: center;
                    line-height: 1.2rem;
                }
            }  
        }

        .sticky {

            .contact {
                padding: 0.5rem;
                display: flex;
                width: 100%;

                @media (min-width: 768px) { // Tablette
                    padding-bottom: 1rem;
                }

                @media screen and (min-width: 1024px) and (max-width: 1439px) { // Laptop
                    padding: 0;
                }
                
                &-gauche {
                    display: flex;
                    flex-direction: column;
                    align-items: center;
                    width: 50%;
                    height: 5rem;

                    .contact-pc {
                        display: none;

                        @media screen and (min-width: 1024px) { // Laptop
                            display: block;
                            color: white;
                        }
                    }

                    @media screen and (min-width: 1024px) and (max-width: 1439px) { // Laptop
                        flex-direction: row;
                        width: 80%;
                        justify-content: space-around;
                        height: 4.5rem;
                    }

                    @media screen and (min-width: 1440px) { // Grand écran
                        flex-direction: row;
                        justify-content: space-around;
                        align-items: center;
                        width: 60%;
                    }
                }

                &-droite {
                    display: flex;
                    flex-direction: column;
                    width: 50%;
                    height: 5rem;

                    @media screen and (min-width: 1024px) and (max-width: 1439px) {
                        flex-direction: row;
                        width: 20%;
                        justify-content: space-around;
                        align-items: center;
                        height: 4.5rem;
                    }

                    @media screen and (min-width: 1440px) {
                        flex-direction: row;
                        justify-content: space-around;
                        align-items: center;
                        width: 40%;
                    }

                    .accueil-mobile {
                        color: var(--clickableElement);

                        @media screen and (min-width: 1024px) and (max-width: 1439px) {
                            display: none;
                        }
                    }
                }

                a {
                    color: white;
                    letter-spacing: 0.05rem;
                    cursor: pointer;
                    text-align: center;
                    margin-bottom: 0.5rem;
                    height: 50%;
                    align-content: center;

                    @media screen and (min-width: 1024px) and (max-width: 1439px) {
                        margin-bottom: 0;
                    }

                    @media screen and (min-width: 1440px) {
                        margin-bottom: 0;
                    }
                }

                &-form {
                    background-color: var(--clickableElement);
                    border-radius: 0.4rem;
                    padding: 0.3rem;

                    @media screen and (min-width: 768px) {
                        padding: 0.2rem 1rem;
                    }
                }

                .form {
                    color: var(--backgroundComponents);
                    font-weight: bold;
                }

                .form, .contact-tel {
                    margin-bottom: 1rem;

                    @media screen and (min-width: 1024px) and (max-width: 1439px) {
                        margin-bottom: 0;
                    }

                    @media screen and (min-width: 1440px) {
                        margin-bottom: 0;
                    }
                }

                &-pc {
                    display: none;
                }
            }

            // Partie Laptop
            .nav {
                display: none;

                @media screen and (min-width: 1024px) and (max-width: 1439px) {
                    display: flex;
                    justify-content: center;
                    padding-bottom: 1rem;
                }

                a {
                    color: var(--clickableElement);
                    // font-size: 0.8rem;
                    letter-spacing: 0.05rem;
                    cursor: pointer; 
                }

                a:active { // Pas tout à fait le bon reprendre celui qu'on a fait sur Yoga
                    border-bottom: 0.2rem solid var(--clickableElement);
                }
            } 
        }  
    }
</style>