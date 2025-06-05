<script>
    import {link} from "svelte-spa-router"
    import { onMount } from 'svelte';

    import logoLinkedIn from ""
    import logo from ""

    // Forcer le défilement après chaque navigation
    onMount(() => {
        const handleScroll = () => {
            window.scrollTo(0, 0);
        };

        // Écoute les changements d'URL (navigations)
        window.addEventListener('sveltekit:navigation-end', handleScroll);

        return () => {
            // Nettoyage à la destruction du composant
            window.removeEventListener('sveltekit:navigation-end', handleScroll);
        };
    });
</script>

<footer>
    <div class="link">
        <div class="link-left">
            <a href="/legal-notices" use:link class="legalNotices" 
                aria-label="Aller à la page des mentions légales" >
                Mention légales
            </a>
            <a href="" 
                class="d" target="_blank"
                aria-label="Ouverture d'une nouvelle page">
            </a>
        </div>

        <a href="/#home" aria-label="Retour à l'accueil">
            <img src={logo} class="logoCabinet " loading="lazy" alt="Logo Cabinet Expertise Auto">
        </a>

        <a href="" 
            aria-label="Ouverture d'une nouvelle page du profil LinkedIn" 
            target="_blank"
            title="Voir le profil LinkedIn">
            <img src={logoLinkedIn} class="logoLinkedIn" alt="Lien pour aller sur le profil LinkedIn">
        </a>
    </div>
    
    <p>© 2025 - Cabinet Expertise Auto. Tous droits réservés.</p>

</footer>

<style lang="scss">
    footer {
        background-color: var(--backgroundComponents);
        background: linear-gradient(135deg, #2b2b3d, #41415c); 
        padding: 0 1rem;

        @media (min-width: 1024px) { // Laptop
            padding: 0 2rem;
        }

        @media (min-width: 1440px) { // Grand écran
            padding: 0 3rem;
        }

        .link {
            display: flex;
            align-items: center;
            justify-content: space-between;

            &-left {
                display: flex;
                flex-direction: column;

                .legalNotices {
                    padding-bottom :0.5rem ;
                }

                .legalNotices, .d {
                    color: white;
                    font-size: 0.7rem;

                    @media (min-width: 768px) { // Tablette
                        font-size: 0.9rem;
                    }

                    @media (min-width: 1024px) { // Laptop
                        font-size: 1rem;
                    }
                }       
            }
            
            .logoCabinet Expertise Auto {
                width: 5rem;

                @media (min-width: 768px) { // Tablette
                    width: 6rem;
                }

                @media (min-width: 1024px) { // Laptop
                    width: 6.5rem;
                }
            }

            .logoLinkedIn {
                width: 1.8rem;

                @media (min-width: 768px) { // Tablette
                    width: 2rem;
                }

                @media (min-width: 1024px) { // Laptop
                    width: 2.5rem;
                }
            }
        }

        p {
            text-align: center;
            color: white;
            font-size: 0.6rem;
            padding-bottom: 0.3rem;

            @media (min-width: 768px) { // Tablette
                font-size: 0.8rem;
            }

            @media (min-width: 1024px) { // Laptop
                font-size: 0.9rem;
            }
        }
    }
</style>