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
        <!-- Invisible pour la partie pc -->
        <a href="" class="contact-form">Contactez-nous ?</a>
        <!--  -->
        <a class="contact-mobile" href="tel:0123456789">01.23.45.67.89</a> <!-- Changer les numéro de téléphone par le sien-->
        <a class="contact-mobile" href="mailto:amaury@gmail.com">amaury@gmail.com</a> <!-- Changer l'email par le sien-->
    </div>
    
    <nav>
        <ul>
            <li>
                <a href="/" use:link aria-label="Retour à l'accueil">Accueil</a>
            </li>
        </ul>
    </nav>
</header>

<style lang="scss">
    header {
        background-color: var(--backgroundComponents);
        background: linear-gradient(135deg, #2b2b3d, #41415c);
        display: flex;
        flex-direction: column;

        .entreprise {
            display: flex;
            align-items: center;

            img {
                width: 7.3rem;
            }

            &-name {
                
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
            padding: 0 0.5rem;
            display: flex;
            &-pc {
                display: none;
            }

            &-form {
                color: var(--clickableElement);
            }

            &-mobile {
                color: white;
            }
        }

        nav {
            ul {
                li {
                    a {
                        color: white;
                    }
                }
            }
        }
    }

</style>