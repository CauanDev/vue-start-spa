<template>
    <br><br><br>
<div class='container'>
        <h1>Hello Vue</h1> 
        <p>You are at {{title}}, and are using {{modo}}</p> 
</div>    


</template>

<script>
export default{
    props: ['title','modo']
}
</script>