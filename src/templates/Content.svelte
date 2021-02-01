<script lang="ts">
    import ContentItem from '../types/ContentItem.ts'
    let url: string | undefined = '';
    let title: string | undefined = '';
    let contentItems: Array<ContentItem> = [];

    chrome.tabs.query({active: true, currentWindow: true}, (tabs) => {
        const currentTab = tabs[0];
        title = currentTab.title;
        url = currentTab.url;
        contentItems = [
            {
                title: 'Title',
                text: title
            },
            {
                title: 'URL',
                text: url
            },
            {
                title: 'Text to be copied',
                text: `${title}<br/>${url}`
            }
        ]
    });
</script>

<div>
    {#each contentItems as contentItem}
        <div>
            <h2>{contentItem.title}</h2>
            <p>{@html contentItem.text}</p>
        </div>
    {/each}
</div>

<style>
    .title {
        text-align: center;
        font-size: 12px;
        background-color: #c71585;
        margin: 0;
        padding: 2px;
    }
</style>
