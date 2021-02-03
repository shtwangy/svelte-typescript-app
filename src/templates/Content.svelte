<script lang="ts">
    import Button from './ButtonContent.svelte'

    let url: string | undefined = '';
    let title: string | undefined = '';

    type ContentItem = {
        title: string;
        text: string | undefined;
    }
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

<div class="content">
    {#each contentItems as contentItem}
        <div>
            <h2 class="content-title">{contentItem.title}</h2>
            <p>{@html contentItem.text}</p>
        </div>
    {/each}
    <Button {url} {title}/>
</div>

<style>
.content {
    padding: 8px;
}
.content-title {
    color: #c71585;
}
</style>
