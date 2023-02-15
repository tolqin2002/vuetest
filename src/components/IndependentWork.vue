<template>
  <div v-for="comment in comments" :key="comment.id">
    <div class="div">
        {"id": {{ comment.id }},
        "product_type_id": {{ comment.product_type_id }},
        "name_uz": {{ comment.name_uz }},
        "cost": {{ comment.cost }},
        "address": {{ comment.address }},
        "created_date": {{ comment.created_date }}}
    </div>
  </div>
</template>

<script>
export default {
    data() {
        return {
            comments: []
        };
    },
    
    methods: {
        async Parameters() {
            try {
                const result = await fetch('http://94.158.54.194:9092/api/product')
                const data = await result.json();
                data.forEach(el => {
                    this.comments.push(el)
                });
            } catch (error) {
                
            }
        }
    },
    created() {
        this.Parameters()
    },
}
</script>
<style>
.div {
    display: flex;
}
</style>