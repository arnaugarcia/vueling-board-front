<script>
    import MenuComponent from '/src/layout/menu.svelte';
    import FooterComponent from '/src/layout/footer.svelte';
    import NavbarComponent from '/src/layout/navbar.svelte';
</script>
<div class="layout-wrapper layout-content-navbar">
    <div class="layout-container">

        <MenuComponent />

        <!-- Layout container -->
        <div class="layout-page">
            <!-- Navbar -->

            <NavbarComponent/>

            <!-- Content wrapper -->
            <div class="content-wrapper">
                <!-- Content -->
                <div class="container-xxl flex-grow-1 container-p-y">
                    <slot></slot>
                </div>
                <!-- / Content -->

                <FooterComponent/>

                <div class="content-backdrop fade"></div>
            </div>
            <!-- Content wrapper -->
        </div>
        <!-- / Layout page -->
    </div>

    <!-- Overlay -->
    <div class="layout-overlay layout-menu-toggle"></div>

    <!-- Drag Target Area To SlideIn Menu On Small Screens -->
    <div class="drag-target"></div>
</div>
