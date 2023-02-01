<template>
    <div class="footer">
        <div class="left">
            <span>Made By <a :href="link" target="_blank">Emerson Braun</a> - {{ new Date().getFullYear() }}</span>
        </div>
        <div class="right">
            <span>
                <a :href="github" target="_blank">
                    <img class="github" src="https://img.icons8.com/material-outlined/24/000000/github.png" alt="Github" />
                </a>
            </span>
        </div>
    </div>
</template>

<script>


export default {
    data() {
        return {
            link: 'https://www.linkedin.com/in/emerson-braun/',
            github: 'https://github.com/EmersonBraun/quotes'
        }
    },
}
</script>

<style>
@media (max-width: 600px) {
    .footer {
        flex-direction: column;
    }

    .left {
        align-self: flex-start;
        max-width: 70%;
    }

    .right {
        align-self: flex-end;
    }
}

@media (min-width: 600px) {
    .footer {
        flex-direction: row;
    }

    .left {
        align-self: center;
    }

    .right {
        align-self: flex-end;
    }
}

.footer {
    position: fixed;
    bottom: 0;
    width: 100%;
    min-height: 50px;
    background-color: rgba(0, 0, 0, .2);
    color: #FFF;
    display: flex;
    justify-content: space-between;
}

.left {
    align-self: flex-start;
}

.right {
    align-self: flex-end;
}

.github {
    width: 50px;
    height: 50px;
}

a {
    color: #FFF;
    text-decoration: none;
}
</style>