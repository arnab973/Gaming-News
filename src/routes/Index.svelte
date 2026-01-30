<script>
// @ts-nocheck

    // Todo: Security test (text overflow, layout overflow, right position, responsivity etc)
    // Todo: Responsivity (follow mobile-first principles)
    // Todo: Add Black and White themes
    // Todo: Add class "uppercase" to the titles that need all the letters to be uppercase

    import { title }     from '.././stores.js';
    import Header        from '.././components/Header.svelte';
    import MainArticle   from '.././components/landing_page/MainArticle.svelte';
    import SimpleSection from '.././components/SimpleSection.svelte';
    import BulletTipItem from '.././components/landing_page/BulletTipItem.svelte';
    import PopUpArticle  from '.././components/PopUpArticle.svelte';
    import MidArticle    from '.././components/landing_page/MidArticle.svelte';
    import CategoryBar   from '.././components/landing_page/CategoryBar.svelte';
    import Footer from '.././components/Footer.svelte';

    import isInViewport from '../assets/js/isInViewport.js';

    window.addEventListener("scroll", (e) => {
        let element = document.getElementById("goc-underline");
        if (isInViewport(element)) {
            element.classList.remove("w-0");
            element.classList.add("w-[75%]");
        }
    });

    let values = [
        {
            imgSrc: "", 
            gameName: "", 
            categoryPage: "", 
            articleTitle: "", 
            authorName: "", 
            articleDate: "", 
            authorPage: "", 
            articlePage: ""
        },
        {
            title: "",
            seeAllPage: "",
            contents: [
                {name: "", icon: "", image: ""},
                {name: "", icon: "", image: ""},
                {name: "", icon: "", image: ""},
                {name: "", icon: "", image: ""},
                {name: "", icon: "", image: ""},
                {name: "", icon: "", image: ""},
                {name: "", icon: "", image: ""},
                {name: "", icon: "", image: ""},
                {name: "", icon: "", image: ""}
            ]
        },
        [
            {
                title: "Newest Posts",
                seeAllPage: "",
                contents: [
                    {
                        gameName: "Elden Ring",
                        title: "How to defeat Margit",
                        authorPhotoSrc: "static/media/images_autores/barbara.png",
                        authorName: "Barbara",
                        postDate: "29.1.26",
                        articlePage: "article/1",
                        imgSrc: "static/media/img/eldenRingImage.svg"
                    },
                    {
                        gameName: "Minecraft",
                        title: "Building a castle",
                        authorPhotoSrc: "static/media/images_autores/fellipe.png",
                        authorName: "Fellipe",
                        postDate: "29.1.26",
                        articlePage: "article/2",
                        imgSrc: "static/media/img/BulletTipIcons/minecraft_logo_icon_168974.webp"
                    },
                    {
                        gameName: "God of War",
                        title: "Boss fight tips",
                        authorPhotoSrc: "static/media/images_autores/henrique.jpeg",
                        authorName: "Henrique",
                        postDate: "29.1.26",
                        articlePage: "article/3",
                        imgSrc: "god-of-war-2018-004-1060x596.jpg"
                    },
                    {
                        gameName: "Multiversus",
                        title: "Character guide",
                        authorPhotoSrc: "static/media/images_autores/lucas.jpeg",
                        authorName: "Lucas",
                        postDate: "29.1.26",
                        articlePage: "article/4",
                        imgSrc: "static/media/img/Multiversus/multiversusImage.png"
                    },
                ]
            },
            {
                title: "Relevant Posts",
                seeAllPage: "",
                contents: [
                    {
                        gameName: "Final Fantasy VII Remake",
                        title: "Ultimate guide",
                        authorPhotoSrc: "static/media/images_autores/matheus.jpeg",
                        authorName: "Matheus",
                        postDate: "29.1.26",
                        articlePage: "article/5",
                        imgSrc: "static/media/img/BulletTipIcons/finalfantasy7r.png"
                    },
                    {
                        gameName: "Fallout 76",
                        title: "Survival tips",
                        authorPhotoSrc: "static/media/images_autores/barbara.png",
                        authorName: "Barbara",
                        postDate: "29.1.26",
                        articlePage: "article/6",
                        imgSrc: "static/media/img/BulletTipIcons/fallout76.png"
                    },
                    {
                        gameName: "Modern Warfare",
                        title: "Weapon tips",
                        authorPhotoSrc: "static/media/images_autores/fellipe.png",
                        authorName: "Fellipe",
                        postDate: "29.1.26",
                        articlePage: "article/7",
                        imgSrc: "static/media/img/BulletTipIcons/modernwarfare.png"
                    },
                    {
                        gameName: "Pokemon Black",
                        title: "Pokemon catching",
                        authorPhotoSrc: "static/media/images_autores/henrique.jpeg",
                        authorName: "Henrique",
                        postDate: "29.1.26",
                        articlePage: "article/8",
                        imgSrc: "static/media/img/BulletTipIcons/pokemonbd.png"
                    },
                ]
            }
        ],
        {
            contents: [
                ["", "", "", ""],
                ["", "", "", ""],
                ["", "", "", ""],
                ["", "", "", ""],
                ["", "", "", ""]
            ]
        }, 
        [
            { 
                gameTitle: "",
                description: "",
                categoryPage: "",
            },
            {
                gameTitle: "",
                description: "",
                categoryPage: "",
            },
            {
                gameTitle: "",
                description: "",
                categoryPage: "",
            }
        ]
    ]

    import { requestApi } from '../api/api_connection.js';

    async function getContent() {
        let payload = await requestApi("index/0");
        let response = await payload.json();

        if (response) {
            values = response;
            // Change postDate to "29.1.26" in new post sections
            values[2].forEach(section => {
                section.contents.forEach(content => {
                    content.postDate = "29.1.26";
                });
            });
        }
    }

    getContent();
</script>

<svelte:head>
    <title>{$title()}</title> 
</svelte:head>

<div class="w-full min-h-screen bg-color-0">
    <Header className="z-50 sticky top-0" />
    <MainArticle {...values[0]} />

    <div class="mt-12">
        <SimpleSection className="mt-8" elementType={BulletTipItem} {...values[1]} />

        <hr class="max-w-[1024px] mx-auto mt-14 mb-20">

        <div class="flex flex-col gap-20 mt-4">
            {#each values[2] as value}
                <SimpleSection elementType={PopUpArticle} {...value} />
            {/each}

            <MidArticle {...values[3]} />
        </div>
    </div>

    <div class="mt-40">
        <div class="w-fit mx-auto">
            <h2 class="text-color-title text-[38px] font-title-regular text-center">TIPS FOR YOUR GAME OF CHOICE</h2>
            <hr id="goc-underline" 
                class="w-0 mx-auto border-[1px] border-[#1E9B8F] dark:border-[#69D3C9] transition-all delay-300 duration-1000">
        </div>

        <div class="flex flex-col gap-[100px] mt-[100px]">
            {#each values[4] as value}
                <CategoryBar {...value} /> 
            {/each}
        </div>
    </div>

    <Footer className="mt-40"/>
</div>


<style>
  
</style>

