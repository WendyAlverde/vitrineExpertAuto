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
</script>

<header class="header {isScrolled ? 'scrolled' : ''}">
    <div class="header-content">
        <div class="entreprise">
            <a href="/" use:link aria-label="Retour à l'accueil"><img src={logoIeta} alt="Logo IETA : Innovation, expertise des technologies automobiles"></a>
            
            <div class="entreprise-name">
                <p class="entreprise-name-titre">Cabinet <em>IETA</em></p>
                <p class="entreprise-name-p">Innovation, Expertise des Technologies Automobiles</p>
            </div>
        </div>
    
        <div class="sticky">
            <div class="contact">
                <a href="/" use:link class="contact-form form">Formulaire Contact</a> <!-- Changer le lien pour amener au formulaire de contact-->
                <!-- Invisible pour la partie mobile -->
                <p class="contact-pc">Amaury Madani</p>
                <!--  -->
                <a class="contact-tel" href="tel:0123456789">01.23.45.67.89</a> <!-- Changer les numéro de téléphone par le sien-->
                <a class="contact-mail" href="mailto:amaury@gmail.com">amaury@gmail.com</a> <!-- Changer l'email par le sien-->
            </div>
        
            <div class="nav">
                <a href="/" use:link aria-label="Aller sur la page d'accueil">Accueil</a>
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
        
        &.scrolled {
            height: 6rem; // Header réduit après scroll

            .header-content {
                transform: translateY(-5rem); // Décale le contenu vers le haut
                transition: transform 0.6s ease; 
            }
        }

        height: auto; 

        .header-content {
            height: auto; // Taille réelle du contenu 
            transition: transform 0.8s ease; 
        }
        
        .entreprise {
            display: flex;
            align-items: center;

            img {
                width: 7rem;
            }

            &-name { 
                display: flex;
                flex-direction: column;
                align-items: center;

                &-titre {
                    font-weight: bold;
                    font-size: 0.938rem;
                    color: white;
                    letter-spacing: 0.07rem;
                    padding-bottom: 0.2rem;

                    em {
                        letter-spacing: 0.3rem;
                        font-size: 1rem;
                    }
                }

                &-p {
                    font-size: 0.7rem;
                    color: white;
                    letter-spacing: 0.03rem;
                    text-align: center;
                    line-height: 1.2rem;
                }
            }  
        }

        .sticky {

            .contact {

                a {
                    color: white;
                    font-size: 0.8rem;
                    letter-spacing: 0.05rem;
                    cursor: pointer;
                }

                &-form {
                    background-color: var(--clickableElement);
                    border-radius: 0.4rem;
                    padding: 0.3rem 0.55rem;
                }

                .form {
                    color: var(--backgroundComponents);
                    font-weight: bold;
                }

                &-pc {
                    display: none;
                }
            }

            .nav {

                a {
                    color: var(--clickableElement);
                    font-size: 0.8rem;
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