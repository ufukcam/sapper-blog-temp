<script context="module">
    export function preload({params, query}) {
        return this.fetch(`blog.json`).then(r => r.json()).then(posts => {
            return {posts};
        });
    }
</script>
<script>
    export let posts;
</script>
<style>
    .home-container {
        align-items: center;
        display: flex;
        flex: 1;
        justify-content: center;
        margin: 2em 0;
        min-height: 400px;
    }

    .home-copy {
        flex: 1;
    }

    h1 {
        font-weight: 700;
        margin-bottom: 0.5em;
    }

    p {
        font-size: 1.4em;
        line-height: 1.5;
    }

    figure {
        margin: 0 1em;
        text-align: center;
    }

    figcaption {
        font-size: .8em;
        font-style: italic;
    }

    img {
        width: 100%;
        max-width: 400px;
    }

    @media (max-width: 1020px) {
        p {
            font-size: 1.2em;
        }

        img {
            max-width: 300px;
        }
    }

    @media (max-width: 800px) {
        .home-container {
            flex-direction: column;
        }

        .home-copy {
            flex: 0;
            padding-bottom: 2em;
            text-align: center;
        }
    }
</style>

<svelte:head>
    <title>Sapper Blog Template</title>
</svelte:head>

<div class="container">
    <div class="home-copy">
        <h1>Welcome!</h1>
        {#each posts as post, index}
            {#if index}
                <hr/>
            {/if}
            <div class="post-item">
                <h2>
                    <a rel='prefetch' href='/{post.slug}'>{post.title}</a>
                </h2>
                <p>{post.excerpt}</p>
                <div class="post-item-footer">
                    <span class="post-item-date">— {post.printDate}</span>
                </div>
            </div>
        {/each}


    </div>
</div>
