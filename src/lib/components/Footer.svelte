<script>
    import {link} from "svelte-spa-router"
    import { onMount } from 'svelte';

    import logoLinkedIn from "../../assets/pictures/logoLinkedin.svg"
    import logoIeta from "../../assets/pictures/logoIetaGood.svg"

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
            <a href="/legalNotices" use:link  class="legalNotices" aria-label="Aller à la page mention légales" >Mention légales</a>
            <a href="http://cfea-expertauto.fr/wp-content/uploads/2014/07/Code-de-déontologie-Experts-en_automobile_adopte_par-CFEA_5avril2016.pdf" class="deontologie" target="_blank">Déontologie</a>
        </div>
        <a href="/#home" aria-label="Retour à l'accueil"><img src={logoIeta} class="logoIeta" loading="lazy" alt="Logo IETA : Innovation, expertise des technologies automobiles"></a>
        <a href="https://www.linkedin.com/in/amaury-m-5638a1192/" aria-label="Ouverture d'une nouvelle page du profil LinkedIn d'Amaury Madani" target="_blank"><img src={logoLinkedIn} class="logoLinkedIn" alt="Lien pour aller sur le profil LinkedIn d'Amaury Madani"></a>
    </div>
    
    <p>© 2025 - IETA. Tous droits réservés.</p>

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

                .legalNotices, .deontologie {
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
            
            .logoIeta {
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