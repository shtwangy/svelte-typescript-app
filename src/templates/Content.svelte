<script lang="ts">
    let url: string | undefined = '';
    let title: string | undefined = '';
    chrome.tabs.query({active: true, currentWindow: true}, (tabs) => {
        const currentTab = tabs[0];
        url = currentTab.url;
        title = currentTab.title;
    });
</script>

<div>
    <h2>Title</h2>
    <p>{title}</p>
</div>
<div>
    <h2>URL</h2>
    <p>{url}</p>
</div>
<div>
    <h2>Text to be copied</h2>
    <p>{title}<br/>{url}</p>
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
