<!--
    Selfie2Anime <https://selfie2anime.com>
    Copyright (c) 2019 by SilentByte <https://www.silentbyte.com/>
-->

<!--suppress HtmlUnknownAnchorTarget, CheckEmptyScriptTag -->
<template>
    <div id="home">
        <!-- Navigation -->
        <nav id="mainNav"
             class="navbar navbar-expand-lg navbar-light fixed-top py-3">
            <div class="container">
                <a href="#home" class="navbar-brand js-scroll-trigger">
                    Selfie2Anime <span class="navbar-brand-inverted">アニメ</span>
                </a>
                <button class="navbar-toggler navbar-toggler-right" type="button" data-toggle="collapse"
                        data-target="#navbarResponsive" aria-controls="navbarResponsive" aria-expanded="false"
                        aria-label="Toggle navigation">
                    <span class="navbar-toggler-icon"></span>
                </button>
                <div class="collapse navbar-collapse" id="navbarResponsive">
                    <ul class="navbar-nav ml-auto my-2 my-lg-0">
                        <li class="nav-item">
                            <a href="#home" class="nav-link js-scroll-trigger">Home</a>
                        </li>
                        <li class="nav-item">
                            <a href="#about" class="nav-link js-scroll-trigger">About</a>
                        </li>
                        <li class="nav-item">
                            <a href="#portfolio" class="nav-link js-scroll-trigger">Portfolio</a>
                        </li>
                        <li class="nav-item">
                            <a href="#contact" class="nav-link js-scroll-trigger">Contact</a>
                        </li>
                    </ul>
                </div>
            </div>
        </nav>

        <!-- Masthead -->
        <header class="masthead">
            <div class="container h-100">
                <div class="row h-100 align-items-center justify-content-center">
                    <div class="col-lg-10 align-self-center">
                        <PhotoUploader />
                    </div>
                </div>
            </div>
        </header>

        <!-- About Section -->
        <section id="about" class="page-section">
            <div class="container carousel-container text-center">
                <h2 class="mt-0">
                    Here's a <span class="text-primary font-weight-bold">quick</span> overview
                </h2>

                <div class="my-5 text-muted" style="line-height: 2em">
                    Using machine learning techniques combined with a
                    <a href="https://en.wikipedia.org/wiki/Generative_adversarial_network">
                        Generative Adversarial Network (GAN)
                    </a> makes it possible to generate <span class="text-primary font-weight-bold">anime-style</span>
                    characters based on real people. Using this website, you can generate your own
                    <span class="text-primary font-weight-bold">anime alter ego</span>!
                    Here are a few examples for you to check out.
                </div>

                <div class="row justify-content-center">
                    <div class="col col-sm-12 col-md-8 col-lg-6">
                        <div class="card shadow-lg">
                            <div class="card-body p-2">
                                <div id="carousel"
                                     class="carousel slide carousel-fade"
                                     data-ride="carousel">
                                    <ol class="carousel-indicators">
                                        <li v-for="i in carouselImageCount"
                                            data-target="#carousel"
                                            :data-slide-to="i"
                                            class="active" />
                                    </ol>
                                    <div class="carousel-inner justify-content-center align-content-center text-center">
                                        <div v-for="i in carouselImageCount"
                                             :key="`carousel-image-${i}`"
                                             :class="['carousel-item', i === 1? 'active':'']">
                                            <img class="d-block w-100"
                                                 :src="`./img/carousel/${i}.jpg`"
                                                 :alt="`Example Image #${i}`">
                                        </div>
                                    </div>
                                    <a class="carousel-control-prev" href="#carousel" role="button"
                                       data-slide="prev">
                                        <span class="carousel-control-prev-icon" aria-hidden="true"></span>
                                        <span class="sr-only">Previous</span>
                                    </a>
                                    <a class="carousel-control-next" href="#carousel" role="button"
                                       data-slide="next">
                                        <span class="carousel-control-next-icon" aria-hidden="true"></span>
                                        <span class="sr-only">Next</span>
                                    </a>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>

                <div class="my-5 text-muted" style="line-height: 2em">
                    Be sure to <a href="#contact" class="js-scroll-trigger">follow us on social media</a>
                    for further updates! If you are interested in how this works, we have made the source code
                    available on Github for both the
                    <a href="https://github.com/SilentByte/selfie2anime-site">front-end</a>
                    and the
                    <a href="https://github.com/t04glovern/selfie2anime">back-end</a>.
                </div>

                <div class="mt-5">
                    <div class="large-caption text-primary">
                        <div class="spinner-grow" style="width: 0.5em; height: 0.5em; margin-bottom: 0.25em;"></div>
                        {{ estimateCounter }}
                        <div class="spinner-grow" style="width: 0.5em; height: 0.5em; margin-bottom: 0.25em;"></div>
                    </div>
                    <div class="text-primary text-uppercase mt-4">selfies &amp; counting</div>
                </div>

                <div class="my-5 text-muted" style="line-height: 2em">
                    The GAN we are using is based on original work by Junho Kim, Minjae Kim, Hyeonwoo Kang, and
                    Kwanghee Lee. Their repository is <a href="https://github.com/taki0112/UGATIT">available here</a>.
                </div>
            </div>
        </section>

        <!-- Action Section -->
        <section id="action" class="page-section bg-dark">
            <div class="container">
                <div class="row justify-content-center">
                    <div class="col-lg-8 text-center text-light py-5">
                        <h2 class="mt-0">
                            What do <span class="text-primary font-weight-bold">YOU</span>
                            look like in <span class="text-primary font-weight-bold">anime</span>?
                        </h2>
                        <a href="#home"
                           class="mt-5 btn btn-primary px-5 btn-xl js-scroll-trigger"
                           style="font-size: 2rem">
                            Give it a try!
                        </a>
                    </div>
                </div>
            </div>
        </section>

        <!-- Portfolio Section -->
        <section id="portfolio" class="bg-dark">
            <div class="container-fluid p-0">
                <div class="row no-gutters">
                    <div v-for="i in 96"
                         class="col-lg-1 col-md-2 col-sm-3 col-4">
                        <a class="portfolio-box" :href="`./img/portfolio/composite/${i}.jpg`">
                            <img class="img-fluid mx-auto d-block"
                                 :src="`./img/portfolio/gan/${i}.jpg`" alt="">
                            <div class="portfolio-box-caption">
                                <img class="img-fluid" :src="`./img/portfolio/original/${i}.jpg`" alt="">
                            </div>
                        </a>
                    </div>
                </div>
            </div>
        </section>

        <!-- Contact Section -->
        <section id="contact" class="page-section">
            <div class="container">
                <div class="row justify-content-center mb-4">
                    <div class="col-lg-8 text-center">
                        <h2 class="mt-0">Want to get in touch?</h2>
                        <hr class="divider my-4">
                        <p class="text-muted mb-5">
                            Follow us on Twitter and Github to find out what other
                            projects we're working on or drop us an email if you
                            have any questions!
                        </p>
                    </div>
                </div>
                <div class="row">
                    <div class="col-lg-4 ml-auto text-center mb-5 mb-lg-0">
                        <i style="color: #38a1f3" class="fa fa-twitter fa-5x mb-3"></i>
                        <a class="d-block" href="https://twitter.com/RicoBeti">@RicoBeti</a>
                        <a class="d-block" href="https://twitter.com/nathangloverAUS">@nathangloverAUS</a>
                    </div>

                    <div class="col-lg-4 ml-auto text-center mb-5 mb-lg-0">
                        <i style="color: #211f1f" class="fa fa-github fa-5x mb-3"></i>
                        <a class="d-block" href="https://github.com/SilentByte">@SilentByte</a>
                        <a class="d-block" href="https://github.com/t04glovern">@t04glovern</a>
                    </div>

                    <div class="col-lg-4 ml-auto text-center mb-5 mb-lg-0">
                        <i style="color: #f06292" class="fa fa-envelope fa-5x mb-3"></i>
                        <a class="d-block" href="mailto:info@selfie2anime.com">info@selfie2anime.com</a>
                    </div>
                </div>
            </div>
        </section>

        <!-- Footer -->
        <footer class="bg-light py-5">
            <div class="container">
                <div class="small text-center text-muted">
                    <a href="https://selfie2anime.com/terms.html" target="_blank">
                        Terms of Service
                    </a>
                    &bull;
                    <a href="https://selfie2anime.com/privacy.html" target="_blank">
                        Privacy Statement
                    </a>
                </div>

                <hr />

                <div class="small text-center text-muted">
                    Copyright &copy; 2019 by
                    <a href="https://twitter.com/RicoBeti">Rico Beti</a>
                    &amp;
                    <a href="https://twitter.com/nathangloverAUS">Nathan Glover</a>
                </div>
            </div>
        </footer>
    </div>
</template>

<!--suppress JSMethodCanBeStatic, JSUnusedGlobalSymbols, TypeScriptCheckImport -->
<script lang="ts">
    import {
        Component,
        Vue,
    } from "vue-property-decorator";

    import axios from "axios";
    import * as creative from "@/vendor/creative";

    import PhotoUploader from "@/components/PhotoUploader.vue";

    @Component({
        components: {
            PhotoUploader,
        },
    })
    export default class Home extends Vue {
        carouselImageCount = 22;
        counter = 0;
        estimateCounter = 0;
        counterTimestamp = 0;
        selfiesPerSecond = 0;
        counterIntervalHandle = 0;

        onUpdateCounter() {
            this.estimateCounter = Math.ceil(
                this.counter
                + (Date.now() / 1000 - this.counterTimestamp)
                * this.selfiesPerSecond,
            );
        }

        async fetchStats() {
            // TODO: Replace current manually calculated estimates with actual real-time numbers once backend is done.
            this.counter = 12052;
            this.selfiesPerSecond = 0.03568;
            this.counterTimestamp = 1566112917;
            this.estimateCounter = this.counter;

            if(this.counterIntervalHandle) {
                clearInterval(this.counterIntervalHandle);
            }

            this.onUpdateCounter();
            this.counterIntervalHandle = setInterval(this.onUpdateCounter, 4000);

            // try {
            //     const response = await axios.get(process.env.VUE_APP_API_COUNT_URL);
            //     this.counter = parseInt(response.data["count"]);
            //     this.selfiesPerSecond = parseFloat(response.data["sps"]);
            //     this.counterTimestamp = Date.now();
            //     this.estimateCounter = this.counter;
            //
            //     if(this.counterIntervalHandle) {
            //         clearInterval(this.counterIntervalHandle);
            //     }
            //
            //     this.onUpdateCounter();
            //     this.counterIntervalHandle = setInterval(this.onUpdateCounter, 4000);
            // } catch(e) {
            //     // tslint:disable-next-line
            //     console.log(e);
            // }
        }

        mounted() {
            this.fetchStats();
            creative.init(jQuery);
        }

        beforeDestroy() {
            if(this.counterIntervalHandle) {
                clearInterval(this.counterIntervalHandle);
            }
        }
    }
</script>

<style lang="scss" scoped>
    $carousel-size: 100px;

    section h2, .large-caption {
        font-size: 2.8em;
        line-height: 1.25;
    }

    .nav-item, .page-section h2 {
        text-transform: uppercase;
    }

    .nav-item .nav-link {
        font-size: 1.2rem !important;
    }

    #mainNav .navbar-brand {
        font-size: 1.7rem !important;
        color: rgba(255, 255, 255, 0.7);
    }

    #mainNav .navbar-brand-inverted {
        color: #f06292;
    }

    #mainNav {
        background: rgba(30, 30, 30, 0.8);
    }

    #mainNav.navbar-scrolled {
        background: #fff;

        .navbar-brand {
            color: #f06292;
        }

        .navbar-brand-inverted {
            color: #212529;
        }
    }

    #portfolio .container-fluid {
        max-width: 12 * 256px;
    }

    .portfolio-box-caption {
        -webkit-transition: opacity 0.75s ease !important;
        transition: opacity 0.75s ease !important;;
    }
</style>
