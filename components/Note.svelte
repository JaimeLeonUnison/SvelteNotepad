<script>
    export let title;
    export let color;
    export let text;
    export let id;


    import { createEventDispatcher } from 'svelte';

    const dispatch = createEventDispatcher();   

    function handleChange() {
        dispatch('update', {
            id: id,
            text: text,
            color: color,
            title: title
        });
    }
</script>

<div class="Note">
    <div class="Note-container" style={'background-color:' +color}>
        <div class="header">
            <div class="options">
                <button><svg xmlns="http://www.w3.org/2000/svg" height="30" viewBox="0 96 960 960" width="30"><path d="M480 976q-82 0-155-31.5t-127.5-86Q143 804 111.5 731T80 576q0-85 32-158t87.5-127q55.5-54 130-84.5T489 176q79 0 150 26.5T763.5 276q53.5 47 85 111.5T880 529q0 108-63 170.5T650 762h-75q-18 0-31 14t-13 31q0 27 14.5 46t14.5 44q0 38-21 58.5T480 976Zm0-400Zm-233 26q20 0 35-15t15-35q0-20-15-35t-35-15q-20 0-35 15t-15 35q0 20 15 35t35 15Zm126-170q20 0 35-15t15-35q0-20-15-35t-35-15q-20 0-35 15t-15 35q0 20 15 35t35 15Zm214 0q20 0 35-15t15-35q0-20-15-35t-35-15q-20 0-35 15t-15 35q0 20 15 35t35 15Zm131 170q20 0 35-15t15-35q0-20-15-35t-35-15q-20 0-35 15t-15 35q0 20 15 35t35 15ZM480 916q11 0 15.5-4.5T500 897q0-14-14.5-26T471 818q0-46 30-81t76-35h73q76 0 123-44.5T820 529q0-132-100-212.5T489 236q-146 0-247.5 98.5T140 576q0 141 99.5 240.5T480 916Z"/></svg></button>
                <button><svg xmlns="http://www.w3.org/2000/svg" height="30" viewBox="0 96 960 960" width="30"><path d="M261 936q-24.75 0-42.375-17.625T201 876V306h-41v-60h188v-30h264v30h188v60h-41v570q0 24-18 42t-42 18H261Zm438-630H261v570h438V306ZM367 790h60V391h-60v399Zm166 0h60V391h-60v399ZM261 306v570-570Z"/></svg></button>
            </div>
        </div>
        <div class="content">
            <div class="title">
                <input type="text" placeholder="Sin título" bind:value={title} on:change={handleChange}>
            </div>
            <div class="text">
                <textarea  
                bind:value={text}
                cols="30" 
                rows="10" 
                placeholder="Escribir..." 
                on:change={handleChange}></textarea>
            </div>
        </div>
    </div>
</div>
<style>
    .Note{
        background-color: white;
        border-radius: 3px;
        border: solid 2px transparent;
        overflow: hidden;
        height: 400px;
    }
    .Note-container{
        height: 100%;
    }
    .Note:focus-within{
        border: solid 2px #000;
        box-shadow: 0 2px 5px rgba(0,0,0,0.2);
    }
    .header .options {
        display: flex;
        justify-content:space-between;

    }
    .Note .content{
        padding: 0 20px;
    }
    .text textarea{
        width: 100%;
        border: 0;
        outline: none;
        resize: none;
        height: 250px;
    }
    .title input{
        font-size: 22px;
        font-weight: bold;
        padding: 10ox 0;
        outline: none;
        border: none;
            width: 100%;
    }
    button {
        margin: 0;
        border: none;
        background-color: transparent;
        cursor: pointer;
    }
    textarea, input {
        background: transparent;
    }
</style>