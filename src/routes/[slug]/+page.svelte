<script lang="ts">
    import CD from "$lib/components/CD.svelte";



    export let data
    const currentData = data.data.Item

    let loading : boolean = true

    setTimeout(() => {
        loading = false
        console.log(currentData)
    }, 2000)



</script>
    <!-- This will be the single page -->
<div class="absolute
            bottom-8
            -left-1/4 -right-1/4

            md:top-1/4
            translate-y-2/3
            md:translate-y-0
        ">
    <CD class="md:w-5/12" artworkURL={loading ? '/images/logo/OUI-cover.webp' : currentData.images[0].url} />
</div>
{#if loading}
    <div class="flex items-center justify-center grow">

        <h1 class="text-white text-4xl text-center font-koulen font-bold animate-pulse">Creating page...</h1>

    </div>
{:else}
    <div class="grow flex mt-12 md:self-end items-start justify-center md:w-1/2">
        <div class="flex flex-col gap-y-2 font-koulen mb-4 z-50 w-full">
            <h1 class="text-4xl md:text-6xl text-white line-clamp-4">{currentData.name}</h1>
            <!-- track, album or artist -->
            {#if currentData.type !== "artist"}
                <h2 class="text-2xl md:text-4xl text-white">{currentData.album ?? currentData.artists[0].name}</h2>
            {/if}
            {#if currentData.type === "track"}
                <small class="text-white font-koulen">{currentData.artists.map(artist => artist.name).join(", ")}</small>
            {/if}
            <div class="border-b w-full mb-4"></div>
            <div class="flex flex-col gap-y-2">
                <!-- music links -->
                <div class="space-y-3">

                    {#if currentData.spotify}
                        <a href="{currentData.spotify.url}" target="_blank" class="flex justify-between items-center bg-white rounded-full px-4 py-2 font-bold gap-x-4 hover:scale-105 transition-all">
                            <svg width="32" height="33" viewBox="0 0 32 33" fill="none" xmlns="http://www.w3.org/2000/svg" class="transition-colors">
                                <path fill-rule="evenodd" clip-rule="evenodd" d="M0 16.5C0 12.2565 1.68571 8.18687 4.68629 5.18629C7.68687 2.18571 11.7565 0.5 16 0.5C20.2435 0.5 24.3131 2.18571 27.3137 5.18629C30.3143 8.18687 32 12.2565 32 16.5C32 20.7435 30.3143 24.8131 27.3137 27.8137C24.3131 30.8143 20.2435 32.5 16 32.5C11.7565 32.5 7.68687 30.8143 4.68629 27.8137C1.68571 24.8131 0 20.7435 0 16.5ZM21.6 23.54C22.56 24.34 24 22.58 22.56 21.62C18.0387 19.2231 12.7707 18.6505 7.84 20.02C6.72 20.18 6.88 22.1 8 22.1C12.8 21.3 16.96 20.66 21.6 23.54ZM23.2 19.54C17.6 16.5 13.6 16.5 7.68 17.78C6.08 17.78 6.08 15.7 7.36 15.22C10.2095 14.4183 13.1897 14.1894 16.1282 14.5464C19.0667 14.9034 21.9054 15.8393 24.48 17.3C25.6 18.1 24.96 20.18 23.2 19.54ZM24.96 14.74C26.56 15.86 28.16 13.14 26.56 12.18C20.3739 8.86613 13.1324 8.119 6.4 10.1C4.8 10.74 5.6 13.3 6.88 13.14C13.44 11.54 19.68 11.54 24.96 14.74Z" fill="currentColor"/>
                            </svg>
                            <span class="text-xl grow">SPOTIFY</span>
                            <!-- carret left -->
                            <svg width="25" height="25" viewBox="0 0 25 25" fill="none" xmlns="http://www.w3.org/2000/svg">
                                <path d="M8.5 20.2344L15.7188 12.5L8.5 4.76562L9.53125 3.73438L17.7812 12.5L9.53125 21.2656L8.5 20.2344Z" fill="#111111"/>
                            </svg>
                        </a>
                    {/if}

                    {#if currentData.deezer}
                        <a href={currentData.deezer?.url} target="_blank" class="flex justify-between items-center bg-white rounded-full px-4 py-2 font-bold gap-x-4 hover:scale-105 transition-all">
                            <span class="text-xl grow">Deezer</span>
                            <!-- carret left -->
                            <svg width="25" height="25" viewBox="0 0 25 25" fill="none" xmlns="http://www.w3.org/2000/svg">
                                <path d="M8.5 20.2344L15.7188 12.5L8.5 4.76562L9.53125 3.73438L17.7812 12.5L9.53125 21.2656L8.5 20.2344Z" fill="#111111"/>
                            </svg>
                        </a>
                    {/if}

                    <p class="cursor-not-allowed flex justify-between items-center bg-neutral-300 rounded-full px-4 py-2 font-bold gap-x-4">

                        <span class="text-xl grow">Amazon Music</span>
                        <!-- carret left -->
                        <svg width="25" height="25" viewBox="0 0 25 25" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <path d="M8.5 20.2344L15.7188 12.5L8.5 4.76562L9.53125 3.73438L17.7812 12.5L9.53125 21.2656L8.5 20.2344Z" fill="#111111"/>
                        </svg>
                    </p>

                    <p class="cursor-not-allowed flex justify-between items-center bg-neutral-300 rounded-full px-4 py-2 font-bold gap-x-4">
                        <svg width="25" height="30" viewBox="0 0 25 30" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <path d="M11.9067 7.396C15.3334 7.50267 18.2067 3.776 17.7254 0.5C14.5254 0.72 11.2921 4.08133 11.9067 7.396ZM22.7734 25.008C23.6401 23.692 23.9601 23.0227 24.6347 21.5307C19.7454 19.6827 18.9574 12.7693 23.7987 10.12C22.3187 8.276 20.2467 7.21067 18.2921 7.21067C15.7014 7.21067 14.6094 8.444 12.8134 8.444C10.9614 8.444 9.55341 7.216 7.31741 7.216C5.11741 7.216 2.77608 8.55333 1.29741 10.8333C-0.793257 14.0467 -0.435924 20.0867 2.94808 25.2413C4.15741 27.076 5.77341 29.148 7.88141 29.1667C8.75608 29.1747 9.33874 28.916 9.96941 28.636C11.8681 27.792 13.8027 27.7627 15.6987 28.6293C16.3121 28.9093 16.8814 29.1707 17.7467 29.1627C19.8601 29.1493 21.5667 26.852 22.7734 25.008Z" fill="currentColor"/>
                        </svg>

                        <span class="text-xl grow">Apple Music</span>
                        <!-- carret left -->
                        <svg width="25" height="25" viewBox="0 0 25 25" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <path d="M8.5 20.2344L15.7188 12.5L8.5 4.76562L9.53125 3.73438L17.7812 12.5L9.53125 21.2656L8.5 20.2344Z" fill="#111111"/>
                        </svg>
                    </p>

                    <p class="cursor-not-allowed flex justify-between items-center bg-neutral-300 rounded-full px-4 py-2 font-bold gap-x-4">
                        <svg width="32" height="33" viewBox="0 0 32 33" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <g clip-path="url(#clip0_4_781)">
                                <path d="M1.54587 16.7628C1.47747 16.7628 1.4215 16.8171 1.41267 16.8921L1.09814 19.766L1.41267 22.5761C1.4215 22.651 1.47747 22.7057 1.54587 22.7057C1.61329 22.7057 1.66795 22.652 1.67875 22.5764L2.0368 19.7657L1.67875 16.8918C1.66795 16.8155 1.61329 16.7628 1.54587 16.7628Z" fill="currentColor"/>
                                <path d="M0.362632 17.8638C0.296193 17.8638 0.243173 17.9148 0.234336 17.9891L0 19.766L0.234336 21.5127C0.242846 21.5866 0.295866 21.6377 0.362632 21.6377C0.427435 21.6377 0.480128 21.5866 0.490601 21.5133L0.767812 19.766L0.490601 17.9875C0.480128 17.9148 0.427435 17.8638 0.362632 17.8638Z" fill="currentColor"/>
                                <path d="M2.80293 16.1992C2.71849 16.1992 2.65107 16.2653 2.64256 16.3563L2.34375 19.766L2.64256 23.0509C2.65107 23.1423 2.71849 23.208 2.80293 23.208C2.88573 23.208 2.95316 23.1423 2.96297 23.0513L3.30204 19.7656L2.96297 16.356C2.95316 16.2653 2.88573 16.1992 2.80293 16.1992Z" fill="currentColor"/>
                                <path d="M4.07041 16.0789C3.97091 16.0789 3.89007 16.1581 3.88222 16.2634L3.6001 19.767L3.88222 23.1557C3.89007 23.2605 3.97091 23.34 4.07041 23.34C4.16827 23.34 4.24878 23.2605 4.25794 23.1557L4.57835 19.767L4.25794 16.2628C4.24878 16.1581 4.16827 16.0789 4.07041 16.0789Z" fill="currentColor"/>
                                <path d="M5.56259 16.5157C5.55474 16.3962 5.46179 16.3049 5.34789 16.3049C5.23236 16.3049 5.14007 16.3959 5.13287 16.5167L4.86646 19.7666L5.13287 23.1838C5.14007 23.3039 5.23269 23.3952 5.34789 23.3952C5.46211 23.3952 5.55474 23.3039 5.56259 23.1838L5.86468 19.7666L5.56259 16.5157Z" fill="currentColor"/>
                                <path d="M6.63604 14.2411C6.50643 14.2411 6.40039 14.3465 6.39384 14.481L6.1438 19.7683L6.39384 23.1851C6.40072 23.318 6.50676 23.4237 6.63604 23.4237C6.76433 23.4237 6.87037 23.3183 6.87823 23.1842V23.1855L7.161 19.7686L6.87823 14.481C6.87005 14.3465 6.764 14.2411 6.63604 14.2411Z" fill="currentColor"/>
                                <path d="M7.91409 13.0233C7.76911 13.0233 7.65096 13.1405 7.64441 13.2901C7.64441 13.2907 7.4104 19.7867 7.4104 19.7867L7.64474 23.1823C7.65128 23.3312 7.76911 23.4483 7.91409 23.4483C8.0581 23.4483 8.17723 23.3312 8.18345 23.1816V23.1836L8.44822 19.7867L8.18345 13.2901C8.17723 13.1405 8.0581 13.0233 7.91409 13.0233Z" fill="currentColor"/>
                                <path d="M9.24276 12.4362C9.08207 12.4362 8.95148 12.5658 8.94592 12.7307L8.72827 19.77L8.94592 23.1305C8.95181 23.2942 9.08207 23.4235 9.24276 23.4235C9.40248 23.4235 9.53307 23.2942 9.53961 23.1296V23.1315L9.7854 19.7703L9.53961 12.7307C9.53274 12.5658 9.40248 12.4362 9.24276 12.4362Z" fill="currentColor"/>
                                <path d="M10.8855 12.494C10.88 12.3133 10.7376 12.1716 10.5618 12.1716C10.3848 12.1716 10.2424 12.3137 10.2375 12.494L10.0359 19.7699L10.2378 23.1095C10.2427 23.2882 10.3848 23.4296 10.5618 23.4296C10.7376 23.4296 10.8803 23.2882 10.8855 23.1085L11.1127 19.7709L10.8855 12.494Z" fill="currentColor"/>
                                <path d="M11.8908 12.3311C11.6977 12.3311 11.5436 12.4846 11.539 12.6806L11.3538 19.7712L11.5397 23.0785C11.5439 23.2725 11.6977 23.4267 11.8908 23.4267C12.0826 23.4267 12.2368 23.2722 12.242 23.0765V23.0791L12.4508 19.7706L12.242 12.6796C12.2368 12.4839 12.0826 12.3311 11.8908 12.3311Z" fill="currentColor"/>
                                <path d="M13.2306 12.5625C13.0224 12.5625 12.8555 12.7284 12.8516 12.9399L12.6824 19.7713L12.8516 23.0589C12.8555 23.2683 13.0224 23.4336 13.2306 23.4336C13.4384 23.4336 13.605 23.2683 13.6089 23.0566V23.0592L13.7987 19.7723L13.6089 12.9402C13.605 12.7284 13.4384 12.5625 13.2306 12.5625Z" fill="currentColor"/>
                                <path d="M14.8047 11.307C14.7405 11.2634 14.663 11.2379 14.5802 11.2379C14.4997 11.2379 14.4247 11.2625 14.3615 11.3037C14.2506 11.376 14.1763 11.5007 14.1743 11.6428L14.173 11.7194L14.0205 19.7699C14.0205 19.7745 14.1743 23.0375 14.1743 23.0375C14.1743 23.0428 14.175 23.0464 14.1753 23.0513C14.1799 23.1423 14.2143 23.2261 14.2696 23.2925C14.3445 23.3818 14.4561 23.4394 14.5802 23.4394C14.6905 23.4394 14.7909 23.3939 14.8642 23.3206C14.9379 23.2477 14.9844 23.1468 14.9863 23.0349L15.0033 22.7122L15.1575 19.7719L14.9867 11.6424C14.984 11.5027 14.912 11.3796 14.8047 11.307Z" fill="currentColor"/>
                                <path d="M16.1447 10.5362C16.0806 10.4969 16.0046 10.474 15.9244 10.474C15.821 10.474 15.7258 10.5113 15.6508 10.5728C15.5546 10.6524 15.4924 10.7722 15.4905 10.9063L15.4895 10.9509L15.3127 19.7732L15.4031 21.4037L15.4905 22.991C15.4941 23.2257 15.6881 23.4201 15.9244 23.4201C16.1598 23.4201 16.3538 23.2257 16.3571 22.9881V22.9914V22.992L16.5502 19.7735L16.3578 10.9057C16.3555 10.7489 16.2697 10.6118 16.1447 10.5362Z" fill="currentColor"/>
                                <path d="M28.064 15.5758C27.5253 15.5758 27.0102 15.6851 26.5422 15.8811C26.2283 12.3343 23.2539 9.55176 19.6256 9.55176C18.7374 9.55176 17.8724 9.72653 17.1078 10.0221C16.811 10.1373 16.7324 10.2551 16.7295 10.4848V22.9767C16.7324 23.2172 16.919 23.4048 17.1543 23.428C17.1645 23.4293 28.0647 23.428 28.0647 23.428C30.2385 23.428 32.0003 21.6855 32.0003 19.5114C32 17.3379 30.2382 15.5758 28.064 15.5758Z" fill="currentColor"/>
                            </g>
                            <defs>
                                <clipPath id="clip0_4_781">
                                    <rect width="32" height="32" fill="white" transform="translate(0 0.5)"/>
                                </clipPath>
                            </defs>
                        </svg>

                        <span class="text-xl grow">Soundcloud</span>
                        <!-- carret left -->
                        <svg width="25" height="25" viewBox="0 0 25 25" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <path d="M8.5 20.2344L15.7188 12.5L8.5 4.76562L9.53125 3.73438L17.7812 12.5L9.53125 21.2656L8.5 20.2344Z" fill="#111111"/>
                        </svg>
                    </p>

                    <p class="cursor-not-allowed flex justify-between items-center bg-neutral-300 rounded-full px-4 py-2 font-bold gap-x-4">
                        <svg width="32" height="33" viewBox="0 0 32 33" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <path fill-rule="evenodd" clip-rule="evenodd" d="M16 10.14C17.6886 10.1418 19.3073 10.8143 20.5 12.0095C21.6927 13.2047 22.3618 14.8248 22.36 16.5134C22.3583 18.2019 21.6858 19.8206 20.4906 21.0133C19.2953 22.206 17.6753 22.8751 15.9867 22.8734C14.2982 22.8716 12.6795 22.1991 11.4868 21.0039C10.294 19.8087 9.62494 18.1886 9.62671 16.5C9.62848 14.8115 10.3009 13.1928 11.4962 12.0001C12.6914 10.8073 14.3115 10.1383 16 10.14ZM13.5734 19.9934L19.48 16.3534L13.5734 13.02V19.9934Z" fill="currentColor"/>
                            <path fill-rule="evenodd" clip-rule="evenodd" d="M29.3334 16.5C29.3334 20.0362 27.9287 23.4276 25.4282 25.9281C22.9277 28.4286 19.5363 29.8334 16.0001 29.8334C12.4639 29.8334 9.07248 28.4286 6.57199 25.9281C4.07151 23.4276 2.66675 20.0362 2.66675 16.5C2.66675 12.9638 4.07151 9.57241 6.57199 7.07193C9.07248 4.57144 12.4639 3.16669 16.0001 3.16669C19.5363 3.16669 22.9277 4.57144 25.4282 7.07193C27.9287 9.57241 29.3334 12.9638 29.3334 16.5ZM16.0001 9.52669C14.1506 9.52669 12.3769 10.2614 11.0692 11.5691C9.76144 12.8769 9.02675 14.6506 9.02675 16.5C9.02675 18.3495 9.76144 20.1232 11.0692 21.4309C12.3769 22.7387 14.1506 23.4734 16.0001 23.4734C17.8495 23.4734 19.6232 22.7387 20.931 21.4309C22.2387 20.1232 22.9734 18.3495 22.9734 16.5C22.9734 14.6506 22.2387 12.8769 20.931 11.5691C19.6232 10.2614 17.8495 9.52669 16.0001 9.52669Z" fill="currentColor"/>
                        </svg>

                        <span class="text-xl grow">Youtube music</span>
                        <!-- carret left -->
                        <svg width="25" height="25" viewBox="0 0 25 25" fill="none" xmlns="http://www.w3.org/2000/svg">
                            <path d="M8.5 20.2344L15.7188 12.5L8.5 4.76562L9.53125 3.73438L17.7812 12.5L9.53125 21.2656L8.5 20.2344Z" fill="#111111"/>
                        </svg>
                    </p>

                </div>
            </div>

        </div>

    </div>
{/if}
