<template>
    <article class="project glass glass--bg pad--2" :class="{isLoading: !isLoaded}">
        <div class="project__wrapper">
            <header>
                <h3 class="project__heading txt--h txt-1">
                    <a :href="project.link" v-if="project.link" target="_blank" rel="noopener noreferrer">
                        <span class="txt--h">{{ project.name }}</span>

                        <span class="icon icon--stroke icon--sm pad--1">
                            <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24"
                                fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round"
                                stroke-linejoin="round" class="feather feather-external-link">
                                <path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"></path>
                                <polyline points="15 3 21 3 21 9"></polyline>
                                <line x1="10" y1="14" x2="21" y2="3"></line>
                            </svg>
                        </span>
                    </a>
                    <span v-else>{{ project.name }}</span>
                </h3>
                <p class="project__description txt--p">{{ project.description }}</p>

                <div class="project__stats mt--1">
                    <span>{{ project.collaborators.length }} collaborators</span>
                </div>
            </header>

            <div class="project__action-cont">
                <ul class="project__members">
                    <template v-for="(member, index) in project.collaborators" :key="member.id">
                        <li class="project__member" v-if="index <= 1" v-bind:title="member.name"></li>
                    </template>

                    <span v-if="project.collaborators.length - 2 > 0">+{{ project.collaborators.length - 2 }}
                        more</span>
                </ul>

                <button class="project__cta cta cta--main-gradient">View more</button>
            </div>
        </div>

        <div class="skeleton pad--2" v-if="!isLoaded">
            <div class="skeleton__group">
                <div class="skeleton__heading"></div>
                <div class="skeleton__txt"></div>
                <div class="skeleton__txt"></div>
            </div>

            <div class="skeleton__group row">
                <div class="skeleton__circles-cont">
                    <div class="circle"></div>
                    <div class="circle"></div>
                </div>

                <div class="skeleton__btn"></div>
            </div>
        </div>
    </article>
</template>

<script>
    export default {
        name: "ProjectCard",
        props: ['project', 'isLoaded'],
        data() {
            return {
                projectData: {
                }
            }
        },
        methods: {

        },
        mounted() {
            // this.getData()
            this.$emit('IsMounted', true);
        },
        watch: {

        }
    };
</script>

<style lang="scss" scoped>
    @import "@/scss/_utils.scss";

    .project {
        width: 100%;
        min-height: 200px;
        border-radius: $defValpx;

        position: relative;

        &__wrapper {
            display: flex;
            flex-direction: column;
            justify-content: space-between;
            height: 100%;
        }

        &__stats {
            opacity: 0.4;
        }

        &__action-cont {
            display: flex;
            align-items: center;
            justify-content: space-between;
        }

        &__members {
            display: inline-flex;
            align-items: center;

            :nth-child(1) {
                left: 0 !important;
            }
        }

        &__member {
            position: relative;
            width: 28px;
            height: 28px;
            border-radius: 50%;
            background: var(--main-gradient);
            border: 1px solid var(--dark);

            left: -$defValpx;
        }

        &.isLoading {
            .project {
                &__wrapper {
                    opacity: 0;
                }
            }
        }

    }

    .skeleton {
        width: 100%;
        height: 100%;
        position: absolute;
        top: 0;
        left: 0;
        animation: pulse 1s ease-in infinite alternate;
        @extend .project;

        &__heading,
        &__txt,
        &__btn {
            min-height: 20px;
            width: 80%;
            background: var(--bg-2);
            margin-bottom: $defValpx;
            border-radius: $defValpx / 2;
        }

        &__heading {
            height: 30px;
            width: 40%;
        }

        &__btn {
            width: 120px;
            height: 40px;
        }

        &__circles-cont {
            @extend .project__members;

            .circle {
                @extend .project__member;
                background: var(--bg-2);
                border-color: var(--bg);
            }
        }

        &__group {

            // margin-top: $defValpx * 2;
            &.row {
                @extend .project__action-cont;
            }
        }
    }

    @keyframes pulse {
        0% {
            opacity: 0.5;
        }

        100% {
            opacity: 1;
        }
    }
</style>