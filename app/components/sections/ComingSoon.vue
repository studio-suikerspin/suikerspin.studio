<template>
    <div class="coming-soon">
        <div class="coming-soon__inner">
            <div class="coming-soon__logo-wrap">
                <img src="/suikerspin-logo.svg" alt="Suikerspin" class="w-full max-w-[224px]" />
            </div>
            <div class="coming-soon__content">
                <h1 class="page-title">Website coming soon...</h1>
                <div class="page-subtitle title-font">
                    <span>Vragen?</span>
                    <span>info@suikerspin.studio</span>
                </div>
            </div>

            <AppMarquee class="coming-soon__marquee" />
        </div>
    </div>
</template>

<style lang="scss" scoped>
.coming-soon {
    background: var(--off-white);
    height: 100dvh;
    padding: 1rem;

    &__inner {
        position: relative;

        background: var(--accent-bordeaux);
        height: 100%;
        border-radius: 1rem;

        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
    }

    &__logo-wrap {
        position: absolute;
        top: 0;
        left: 0;
        right: 0;

        display: flex;
        justify-content: center;
        align-items: center;
        padding: 2rem;
    }

    &__content {
        display: flex;
        flex-direction: column;
        gap: 40px;
    }

    .page-title {
        max-width: 1050px;
        margin-inline: auto;
        
        color: var(--off-white);
        text-align: center;
        font-size: clamp(3rem, -1.4318rem + 14.1818vw, 7.875rem);
        font-weight: 400;
        line-height: 100%
    }

    .page-subtitle {
        display: flex;
        flex-direction: column;
        gap: 10px;

        color: var(--accent-yellow);
        text-align: center;
        font-size: 18px;
        font-weight: 400;
        line-height: 100%

        span {
            display: block;
        }

        @media (min-width: 768px) {
            font-size: 24px;
        }
    }

    &__marquee {
        position: absolute;
        bottom: 48px;
    }
}
</style>