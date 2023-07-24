<template>
    <div>
        <b-navbar toggleable="lg" type="dark" variant="dark">
            <b-navbar-brand href="/">
                <!-- <img src="https://placekitten.com/g/30/30" alt="Kitten"> -->
                TestVerse
            </b-navbar-brand>
            <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

            <b-collapse id="nav-collapse" is-nav>
                <b-navbar-nav>
                    <!-- <b-nav-item href="/">Home</b-nav-item> -->
                    <!-- <b-nav-item href="/about">About</b-nav-item> -->

                    <!-- Navbar dropdowns -->
                    <b-nav-item-dropdown text="Suites" right>
                        <b-dropdown-item href="/criar-suite">Criar</b-dropdown-item>
                        <b-dropdown-item href="/listar-suites">Consultar</b-dropdown-item>
                        <b-dropdown-item href="#" disabled>Editar</b-dropdown-item>
                        <b-dropdown-item href="#" disabled>Deletar</b-dropdown-item>
                    </b-nav-item-dropdown>

                    <!-- Navbar dropdowns -->
                    <b-nav-item-dropdown text="Casos de Teste" right disabled>
                        <b-dropdown-item href="#">Criar</b-dropdown-item>
                        <b-dropdown-item href="#">Consultar</b-dropdown-item>
                        <b-dropdown-item href="#">Editar</b-dropdown-item>
                        <b-dropdown-item href="#">Deletar</b-dropdown-item>
                    </b-nav-item-dropdown>
                    <b-nav-item-dropdown text="Steps" right disabled>
                        <b-dropdown-item href="#">Criar</b-dropdown-item>
                        <b-dropdown-item href="#">Consultar</b-dropdown-item>
                        <b-dropdown-item href="#">Editar</b-dropdown-item>
                        <b-dropdown-item href="#">Deletar</b-dropdown-item>
                    </b-nav-item-dropdown>
                </b-navbar-nav>
            </b-collapse>
        </b-navbar>
    </div>
</template>