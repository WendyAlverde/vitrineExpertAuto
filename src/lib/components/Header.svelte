<script>
    import { link, location } from "svelte-spa-router"
    import { onMount, onDestroy } from 'svelte';
    import logoIeta from "../../assets/pictures/logoIetaGood.svg"

    // Variables
    let isScrolled = false; 
    let currentPath = "";   

    // ==================== Gère le changement de hauteur du header lors du scroll ==================== //
    const handleScroll = () => {
        isScrolled = window.scrollY > 0;
    };

    onMount(() => {
        // Vérifie si la route actuelle correspond à "Mentions Légales"
        window.addEventListener("scroll", handleScroll);

        // Mise à jour du chemin actuel
        const updatePath = () => {
            currentPath = window.location.hash || "#home";
        };
        window.addEventListener("hashchange", updatePath);
        updatePath(); // Initialisation

        // Nettoyage des événements pour éviter les fuites mémoire
        return () => {
            window.removeEventListener("scroll", handleScroll);
            window.removeEventListener("hashchange", updatePath);
        };
    });

    const scrollToAnchor = (event) => {
        event.preventDefault(); // Empêche le comportement par défaut du navigateur
        const targetId = event.target.getAttribute('href').substring(2); // Ex: "#contactForm" → "contactForm"

        // Vérifie si on est déjà sur la page d'accueil
        if (location.pathname === "/") {
            // Si on est déjà sur la Home, on scrolle directement
            requestAnimationFrame(() => {
                const targetElement = document.getElementById(targetId);
                if (targetElement) {
                    targetElement.scrollIntoView({ behavior: 'smooth' });
                }
            });
        } else {
            // Sinon, on change de page puis on attend le chargement
            window.location.href = `/#${targetId}`;
            
            // Attendre le chargement de la nouvelle route et scroller ensuite
            setTimeout(() => {
                const targetElement = document.getElementById(targetId);
                if (targetElement) {
                    targetElement.scrollIntoView({ behavior: 'smooth' });
                }
            }, 400); // Temps suffisant pour le changement de page
        }
    };

    // let currentPath = window.location.hash || "#home";

    onMount(() => {
        window.addEventListener("hashchange", () => {
            currentPath = window.location.hash || "#home";
        });
    });
</script>

<header class="header {isScrolled ? 'scrolled' : ''}">
    <div class="header-content">
        <div class="entreprise">
            <a href="#home" aria-label="Retour à l'accueil" class="logoIeta">
                <!-- <img src={logoIeta} alt="Logo IETA : Innovation, expertise des technologies automobiles"> -->
            </a>
            
            <div class="entreprise-name">
                <p class="entreprise-name-titre">Cabinet <em>IETA</em></p>
                <p class="entreprise-name-p">Innovation, Expertise des Technologies Automobiles</p>
            </div>
        </div>
    
        <div class="sticky" role="navigation" aria-label="Menu principal">
            <div class="contact">
                <div class="contact-gauche ">
                    <!-- Title permet d'ajouter une infobulle -->
                    <a href="/#contactForm" class="contact-form form" on:click={scrollToAnchor} 
                        aria-label="Aller au formulaire de contact (défilement automatique)" title="Aller au formulaire de contact">
                        Formulaire Contact
                    </a>
                    <!-- Invisible pour la partie mobile -->
                    <p class="contact-pc">Amaury Madani</p>
                    <a class="contact-mail" href="mailto:cabinet.ieta@outlook.fr" target="_blank" 
                        aria-label="Ouvrir votre application mail pour écrire à cabinet.ieta@outlook.fr">
                        cabinet.ieta@outlook.fr
                    </a>
                </div>
                <div  class="contact-droite">
                    <a class="contact-tel" href="tel:0628406288"
                        aria-label="Appeler le 06 28 40 62 88">
                        06 28 40 62 88
                    </a>
                    <a class="accueil-mobile {currentPath === '#home' ? 'active' : ''}" 
                        href="#home" 
                        aria-current="{currentPath === '#home' ? 'page' : undefined}" 
                        aria-label="Aller sur la page d'accueil"
                        title="Retour à l'accueil">
                        Accueil
                    </a>
                </div>
            </div>

            <!-- Partie Laptop -->
            <div class="nav">
                <a class="tablette {currentPath === '#home' ? 'active' : ''}" 
                    href="#home" 
                    aria-current="{currentPath === '#home' ? 'page' : undefined}" 
                    aria-label="Aller sur la page d'accueil"
                    title="Retour à l'accueil">
                    Accueil</a>
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
            height: 5rem; // Header réduit après scroll

            @media (min-width: 768px) { // Tablette
                height: 6.5rem;
            }

            @media screen and (min-width: 1024px) and (max-width: 1439px) { // Laptop
                height: 7rem;
            }

            @media screen and (min-width: 1440px) { // Laptop
                height: 5.5rem;
            }

            .header-content {
                background: linear-gradient(135deg, #2b2b3d, #41415c);
                transform: translateY(-5.5rem); // Décale le contenu vers le haut
                transition: transform 0.6s ease; 

                @media screen and (min-width: 768px) { // Laptop
                    transform: translateY(-5.8rem); // Décale le contenu vers le haut
                }

                @media screen and (min-width: 1024px) { // Laptop
                    transform: translateY(-6.2rem); // Décale le contenu vers le haut
                }
            }
        }

        .header-content {
            height: auto; // Taille réelle du contenu 
            transition: transform 0.8s ease; 

            .entreprise {
                display: flex;
                align-items: center;
                padding: 0 0.5rem;
                position: relative;

                @media (min-width: 768px) { // Tablette
                    padding-bottom: 0.3rem;
                }

                @media (min-width: 1024px) { // Laptop
                    padding-bottom: 0.8rem;
                }

                a {
                    display: block;
                    position: absolute;
                    // top: 0;
                    top: -0.5rem;
                    left: 0;

                    // Essai 2 pour img flou sur iphone
                    background-image: url('../../assets/pictures/logoIetaGood.svg'); // Remplacez par le chemin de votre image
                    background-size: contain; // Ajuste l'image pour qu'elle soit entièrement visible
                    background-repeat: no-repeat; // Évite que l'image se répète
                    background-position: center; // Centre l'image
                    width: 7rem; // Largeur de base
                    height: 7rem; // Hauteur de base

                    @media (min-width: 768px) { // Tablette
                        width: 7.5rem;
                        height: 7.5rem;
                    }

                    @media (min-width: 1024px) { // Laptop
                        width: 8rem;
                        height: 8rem;
                    }

                    img {
                        width: 7rem;
                    // Essai 1 pour img flou sur iphone
                    //   image-rendering: -webkit-optimize-contrast;
                    //    image-rendering: crisp-edges;
                    }
                    //     @media (min-width: 768px) { // Tablette
                    //         width: 7.5rem;
                    //     }

                    //     @media (min-width: 1024px) { // Laptop
                    //         width: 8rem;
                    //     }
                    // }
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
                // Une ligne ombrée pour faire resortir les liens
                box-shadow: 0px -4px 10px rgba(0, 0, 0, 0.3);

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
                        width: 60%;
                        height: 5rem;
                        
                        .contact-pc {
                            display: none;

                            @media screen and (min-width: 1024px) { // Laptop
                                display: block;
                                color: white;
                            }
                        }

                        .contact-mail {
                            padding-left: 1rem;
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
                        align-items: center;
                        gap: 8rem;
                        padding-bottom: 1rem;
                    }

                    a {
                        color: var(--clickableElement);
                        letter-spacing: 0.05rem;
                        cursor: pointer; 
                        // border-bottom: 0.2rem solid var(--clickableElement);
                    }
                } 
            }  
        }
    }
</style>