# Burger

``` svelte
<script>
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
```

``` html
    <button class="burger" aria-pressed={menuOpen} aria-label={menuOpen ? "Fermer le menu" : "Ouvrir le menu" on:click={toggleMenu}>
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
```

``` scss
    // Burger
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
```
