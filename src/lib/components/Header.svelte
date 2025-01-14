<script>
    import {link} from "svelte-spa-router"
    
    import logoIeta from "../../assets/pictures/logoIeta.svg"
</script>

<header>
    <div>
        <img src={logoIeta} alt="Logo I.E.T.A : Innovation, expertise des technologies automobiles">
        <p>Cabinet I.E.T.A</p>
        <p>Innovation, expertise des technologies automobiles</p>
    </div>
    <div>
        <!-- Invisible pour la partie mobile -->
        <p>Contactez nous ?</p>
        <p>Amaury Madani</p>
        <!--  -->
        <!-- Invisible pour la partie pc -->
        <a href="">Amaury Madani</a>
        <!--  -->
        <a href="tel:0123456789">01.23.45.67.89</a> <!-- Changer les numéro de téléphone par le sien-->
        <a href="mailto:amaury@gmail.com">amaury@gmail.com</a> <!-- Changer l'email par le sien-->
    </div>
    
    <nav>
        <ul>
            <li>
                <a href="/" use:link aria-label="Retour à l'accueil">Accueil</a>
            </li>
        </ul>
    </nav>
</header>