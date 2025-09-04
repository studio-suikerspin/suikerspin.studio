<script setup>
let observer = null;

function initCSSMarquee() {
    const pixelsPerSecond = 75; // Set the marquee speed (pixels per second)
    const marquees = document.querySelectorAll('[data-css-marquee]');

    // Duplicate each [data-css-marquee-list] element inside its container
    marquees.forEach(marquee => {
        marquee.querySelectorAll('[data-css-marquee-list]').forEach(list => {
            const duplicate = list.cloneNode(true);
            marquee.appendChild(duplicate);
        });
    });

    // Create an IntersectionObserver to check if the marquee container is in view
    observer = new IntersectionObserver(entries => {
        entries.forEach(entry => {
            entry.target.querySelectorAll('[data-css-marquee-list]').forEach(list =>
                list.style.animationPlayState = entry.isIntersecting ? 'running' : 'paused'
            );
        });
    }, { threshold: 0 });

    // Calculate the width and set the animation duration accordingly
    marquees.forEach(marquee => {
        marquee.querySelectorAll('[data-css-marquee-list]').forEach(list => {
            list.style.animationDuration = (list.offsetWidth / pixelsPerSecond) + 's';
            list.style.animationPlayState = 'paused';
        });
        observer.observe(marquee);
    });
}

onMounted(() => {
    initCSSMarquee();
});

onUnmounted(() => {
    observer.disconnect();
})
</script>

<template>
    <div data-css-marquee="" class="marquee-css">
        <div data-css-marquee-list="" class="marquee-css__list">
            <template v-for="i in 10" :key="i"> 
                <div  class="marquee-css__item">
                    <p class="marquee-css__item-p">Open to work</p>
                </div>

                <div class="marquee-css__dot"></div>

                <div  class="marquee-css__item">
                    <p class="marquee-css__item-p">October / November</p>
                </div>

                <div class="marquee-css__dot"></div>
            </template>
        </div>
    </div>
</template>

<style lang="scss" scoped>
.marquee-css {
    color: var(--accent-bordeaux);
    background-color: var(--accent-yellow);
    width: 100%;
    display: flex;
    position: relative;
    overflow: hidden;

    &__list {
        flex: none;
        align-items: center;
        display: flex;
        position: relative;
    }

    &__item {
        flex: 0;
        align-items: center;
        display: flex;
    }

    &__item-p {
        white-space: nowrap;
        margin-bottom: 0;
        font-size: 18px;
    }

    &__dot {
        width: 12px;
        height: 12px;
        background-color: var(--accent-bordeaux);
        border-radius: 50%;

        margin-inline: 48px;
    }
}

/* CSS Keyframe Animation */
@keyframes translateX {
    to {
        transform: translateX(-100%);
    }
}

[data-css-marquee-list] {
    animation: translateX 30s linear;
    animation-iteration-count: infinite;
    animation-play-state: paused;
}
</style>