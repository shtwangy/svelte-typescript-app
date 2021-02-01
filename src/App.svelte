<script lang="ts">
    import Title from './Title.svelte';
    let url: string | undefined = '';
    let title: string | undefined = '';
    chrome.tabs.query({active: true, currentWindow: true}, (tabs) => {
        const currentTab = tabs[0];
        url = currentTab.url;
        title = currentTab.title;
    });
</script>

<div class="container">
    <Title />
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
</div>

<style>
    .container {
        width: 400px;
        padding: 0;
    }
</style>
