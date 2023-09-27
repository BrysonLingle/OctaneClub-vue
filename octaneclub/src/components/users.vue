<!-- <template>
    <h3> Photos </h3>
</template>


<script>
import axios from "axios";

export default {
    name: "photos",
    data() {
        return {
            photos: null,
        };
    },
    created() {
        axios
            .get('https://api.lorem.space/image/game?w=150&h=220')
            .then(res => {
                this.photos = res.data;
            })
            .catch(error => {
                console.error(error);
            });
    },
};
</script> -->
