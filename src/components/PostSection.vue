<template>
    <section class="posts-section">
        <h1>Posts</h1>

            <!-- <post-component>

            </post-component> -->

        <div class="posts">
            <div v-for="post in posts" v-bind:key="post.id">
                <div class="post">
                    <div class="content">
                        <div class="left">
                            <img :src="base_url + 'storage/' + post.user_image" alt="">
                        </div>
                        <div class="right">
                            <h3> {{post.user_name}} </h3>
                            <h5> {{post.followers}} followers</h5>
                            <span> {{post.publication_data}} ore • </span>
                            <span> {{post.post_type}} • </span>
                            <i class="fas fa-globe-americas"></i>
                        </div>    
                    </div>

                    <div class="paragraph">
                        <p> {{post.description}} </p>
                    </div>

                    <div class="image">
                        <img :src="base_url + 'storage/' + post.post_image" alt="">
                    </div>

                    <div class="opinions">
                        <i class="far fa-thumbs-up"></i>
                        <i class="fas fa-sign-language"></i>
                        <i class="far fa-heart"></i>
                    </div>

                    <div class="share">
                        <i class="far fa-thumbs-up"> Consiglia</i>
                        <i class="far fa-comment"> Commenta</i>
                        <i class="fas fa-share"> Condividi</i>
                        <i class="far fa-paper-plane"> Invia</i>
                    </div>

                    <div class="comment">
                        <img :src="base_url + 'storage/' + post.user_image" alt="">
                        <input type="text" name="" id="" placeholder="Aggiungi un commento...">
                    </div>
                </div>
            </div>
        </div>
    </section>
</template>

<script>
import Axios from "axios";
export default {
    data(){
        return {
            base_url: 'http://127.0.0.1:8000/',
            api_endpoint: "api/posts",
            posts: null,
            /* meta: null,
            link: null, */
        }
    },
    mounted(){
        const fullUrl = this.base_url + this.api_endpoint;
        Axios.get(fullUrl).then(resp => {
            console.log(resp);
            this.posts = resp.data.data;
            /* this.meta = resp.data.meta;
            this.links = respo.data.links */
        })
        .catch(e => {
            console.error('Sorry! Something went wrong' + e)
        })
    }
}
</script>

<style lang="scss" scoped>
    .posts{
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    font-family: 'Nunito', sans-serif;
    
    .post{
        width: 600px;
        margin-bottom: 40px;
        border-radius: 10px;
        background-color: white;
        box-shadow: 1px 1px 10px 1px rgb(184, 184, 184);

        .content{
            padding: 20px;
            display: flex;
            justify-content: flex-start;
            text-align: left;


            .left{
                img{
                    height: 50px;
                    width: 50px;
                    border-radius: 50%;
                    cursor: pointer;
                }
            }
            .right{
                line-height: 10px;
                margin-left: 20px;
                color: #666666;

                h3{
                    margin: 0 0 4px 0;
                    font-size: 15px;
                    font-weight: 600;
                    text-transform: capitalize;
                    color: #191919;

                    &:hover{
                        text-decoration: underline;
                    }
                }
                h5{
                    font-size: 12px;
                    margin: 10px 0 4px 0;
                }
                span{
                    font-size: 12px;
                }
            }
        }
        .paragraph{
            padding: 10px 20px 0 20px;
            text-align: left;
            
            p{
                font-size: 20px;
            }
        }
        .image{
            img{
                width: 600px;
                height: 300px;
                cursor: pointer;
            }
        }
        .opinions{
            padding: 20px;
            border-bottom: 1px solid #ebebeb;
            text-align: left;

            .fa-thumbs-up{
                color: #004b7c;
                background-color: #1485bd;
                border-radius: 50%;
                padding: 5px;
                margin-right: 10px;
            }
            .fa-sign-language{
                color: #155208;
                background-color: #6dae4f;
                border-radius: 50%;
                padding: 5px;
                margin-right: 10px;
            }
            .fa-heart{
                color: #77280c;
                background-color: #df704d;
                border-radius: 50%;
                padding: 5px;
            }
        }
        .share{
            padding: 20px;
            color: #666666;
            text-align: left;

            i{
                margin-right: 20px;
                font-size: 20px;
                
                &:hover{
                    cursor: pointer;
                    color: #0a66c2;
                }
            }
        }
        .comment{
            display: flex;
            justify-content: space-around;
            align-items: center;
            padding: 10px 20px 20px 20px ;

            img{
                height: 40px;
                width: 40px;
                border-radius: 50%; 
                cursor: pointer;
            }
            input{
                width: 80%;
                height: 40px;
                padding: 5px 5px 5px 20px;
                border-radius: 50px;
                border: 1px solid #666666;
                outline: none;
            }
        }
    }
}
</style>