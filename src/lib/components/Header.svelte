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

    // ==================== Menu burger ==================== //
    // État pour contrôler l'ouverture du menu
    let menuOpen = false;

    // Fonction pour ouvrir/fermer le menu
    function toggleMenu() {
        menuOpen = !menuOpen;
        // Menu burger ouvert, bloquer le défilement de la page
        document.body.classList.toggle('menu-open', menuOpen);
    }

    // Fonction pour fermer le menu
    function closeMenu() {
        menuOpen = false;
        // Menu burger ouvert, bloquer le défilement de la page
        document.body.classList.remove('menu-open');
    }

    let firstFocusableElement;
    let lastFocusableElement;

    onMount(() => {
        //  Gère les interactions clavier dans le menu
        const handleKeyPress = (event) => {
            if (!menuOpen) return;
            // Ferme le menu si la touche "Échap" est pressée
            if (event.key === "Escape") {
                closeMenu();
            }
            // Gère la navigation au clavier avec la touche "Tab" pour le focus
            if (event.key === "Tab") {
                // Sélectionne tous les éléments pouvant être focalisés dans le menu (liens et bouton)
                const focusableElements = document.querySelectorAll(
                    ".mobile-nav-list a, .mobile"
                );
                // Identifie le premier et le dernier élément du menu
                firstFocusableElement = focusableElements[0];
                lastFocusableElement = focusableElements[focusableElements.length - 1];
                // Si "Shift + Tab" est pressé et qu'on est sur le premier élément,
                // renvoyer le focus au dernier élément (boucle de navigation)
                if (event.shiftKey && document.activeElement === firstFocusableElement) {
                    lastFocusableElement.focus();
                    event.preventDefault();
                // Si "Tab" est pressé sans "Shift" et qu'on est sur le dernier élément,
                // renvoyer le focus au premier élément
                } else if (!event.shiftKey && document.activeElement === lastFocusableElement) {
                    firstFocusableElement.focus();
                    event.preventDefault();
                }
            }
        };
        // Ajoute un écouteur d'événements sur tout le document pour capturer les interactions clavier
        document.addEventListener("keydown", handleKeyPress);
        // Retourne une fonction pour nettoyer l'écouteur lorsque le composant est détruit
        // Par exemple lorsque sa condition {#if} devient false
        return () => document.removeEventListener("keydown", handleKeyPress);
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
        
            <!-- <div class="nav">
                <a href="/" use:link aria-label="Aller sur la page d'accueil">Accueil</a>
            </div> -->
    
            <button class="burger" aria-pressed={menuOpen} aria-label={menuOpen ? "Fermer le menu" : "Ouvrir le menu"} on:click={toggleMenu}>
                <em class="burger__bar"></em>
            </button>
            <!-- Mobile -->
            {#if menuOpen}
            <dialog class="accessibility" aria-modal="true" open>
                <button class="mobile" aria-label="Fermer le menu" on:click="{closeMenu}">
                    <nav class="mobile-nav" >
                        <p>IETA</p>
                        <ul class="mobile-nav-list">
                            <li><a href="/" use:link aria-label="Aller sur la page d'accueil">Accueil</a></li>
                        </ul>
                    </nav>
                </button>
            </dialog>
            {/if}
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

            // .nav {

            //     a {
            //         color: var(--clickableElement);
            //         font-size: 0.8rem;
            //         letter-spacing: 0.05rem;
            //         cursor: pointer; 
            //     }

            //     a:active { // Pas tout à fait le bon reprendre celui qu'on a fait sur Yoga
            //         border-bottom: 0.2rem solid var(--clickableElement);
            //     }
            // }

            // Essaie burger
            .burger {
                background: none;
                border: none;
                width: 2.1rem;
                height: 2.1rem;
                position: relative;
                cursor: pointer;
                display: flex;
                justify-content: center;
                align-items: center;

                @media (min-width: 1020px) { /*Passage du burger*/
                    display: none;
                }
                // La barre du centre
                .burger__bar {
                    display: block;
                    width: 1.3rem;
                    height: 0.15rem;
                    background-color: var(--clickableElement);
                    position: absolute;
                    transition: transform 0.3s ease, opacity 0.3s ease;
                    z-index: 3;

                    // Les barres du dessous et du dessus 
                    &::before,
                    &::after {
                        display: block;
                        content: '';
                        width: 1.25rem;
                        height: 0.15rem;
                        background-color: var(--clickableElement);
                        position: absolute;
                        transition: transform 0.3s ease, opacity 0.3s ease;
                    }

                    &::before {
                        transform: translateY(-0.5rem);
                    }

                    &::after {
                        transform: translateY(0.5rem);
                    }
                }

                // Quand le menu est ouvert transformer le burger en croix
                &[aria-pressed="true"] .burger__bar {
                    background-color: transparent;

                    &::before {
                        transform: rotate(45deg);
                        background-color: var(--backgroundComponents);
                    }

                    &::after {
                        transform: rotate(-45deg);
                        background-color: var(--backgroundComponents);
                    }
                }
            }

            .accessibility {
                background: none;
                border: none;

                .mobile {
                    position: fixed;
                    top: 0;
                    left: 0;
                    width: 100%;
                    height: 100%;
                    background: rgba(0, 0, 0, 0.5); /* Assombrit le reste du site */
                    display: flex;
                    justify-content: flex-end; /* Aligner le menu à droite */
                    z-index: 2; /* Au-dessus de tout */
                        
                    &-nav {
                        width: 50%;
                        max-width: 20rem;
                        background: var(--clickableElement);
                        height: auto; /* Hauteur selon le contenu */
                        padding: 1rem;
                        position: relative;
                        top: 7.5rem;
                        display: flex;
                        flex-direction: column;
                        border-radius: 3%;

                        p {
                            color: var(--backgroundComponents);
                            font-size: 1.5rem;
                            letter-spacing: 0.07rem;
                            font-weight: bold;
                        };

                        &-list {
                            display: flex;
                            flex-direction: column;
                            gap: 1rem;
                            margin: 1rem 0;

                            li {
                                padding: 0.5rem;

                                a {
                                    color: var(--backgroundComponents);
                                    font-weight: bold;
                                    text-decoration: none;
                                    font-size: 1.5rem;
                                }
                            }
                        }
                    }
                }
            }
        }  
    }
</style>