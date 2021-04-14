<template>
    <article class="project glass glass--bg pad--2">
        <header>
            <h3 class="txt--h txt-1">
                <a :href="project.link" v-if="project.link" target="_blank" rel="noopener noreferrer">
                    <span>{{ project.name }}</span>

                    <span class="icon icon--sm">
                        <svg xmlns="http://www.w3.org/2000/svg" viewBox="-3 -3 24 24" width="24" height="24"
                            preserveAspectRatio="xMinYMin" class="jam jam-link">
                            <path
                                d="M3.19 9.345a.97.97 0 0 1 1.37 0 .966.966 0 0 1 0 1.367l-2.055 2.052a1.932 1.932 0 0 0 0 2.735 1.94 1.94 0 0 0 2.74 0l4.794-4.787a.966.966 0 0 0 0-1.367.966.966 0 0 1 0-1.368.97.97 0 0 1 1.37 0 2.898 2.898 0 0 1 0 4.103l-4.795 4.787a3.879 3.879 0 0 1-5.48 0 3.864 3.864 0 0 1 0-5.47L3.19 9.344zm11.62-.69a.97.97 0 0 1-1.37 0 .966.966 0 0 1 0-1.367l2.055-2.052a1.932 1.932 0 0 0 0-2.735 1.94 1.94 0 0 0-2.74 0L7.962 7.288a.966.966 0 0 0 0 1.367.966.966 0 0 1 0 1.368.97.97 0 0 1-1.37 0 2.898 2.898 0 0 1 0-4.103l4.795-4.787a3.879 3.879 0 0 1 5.48 0 3.864 3.864 0 0 1 0 5.47L14.81 8.656z" />
                        </svg>
                    </span>
                </a>
                <span v-else>{{ project.name }}</span>
            </h3>
            <p class="txt--p">{{ project.description }}</p>

            <div class="project__stats mt--1">
                <span>{{ project.collaborators.length }} collaborators</span>
            </div>
        </header>

        <div class="project__action-cont">
            <ul class="project__members">
                <template v-for="(member, index) in project.collaborators" :key="member.id">
                    <li class="project__member" v-if="index <= 1" v-bind:title="member.name"></li>
                </template>

                <span v-if="project.collaborators.length - 2 > 0">+{{ project.collaborators.length - 2 }} more</span>
            </ul>

            <button class="cta cta--main-gradient">View more</button>
        </div>
    </article>
</template>

<script>
    export default {
        name: "ProjectCard",
        props: ['project'],
        data() {
            return {

            }
        }
    };
</script>

<style lang="scss" scoped>
    @import "@/scss/_utils.scss";

    .project {
        width: 100%;
        min-height: 200px;
        border-radius: $defValpx;

        display: flex;
        flex-direction: column;
        justify-content: space-between;

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
                left: 0;
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
    }
</style>