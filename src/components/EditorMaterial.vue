<template>
    <div class="editor-material">
        <!-- 左侧一级菜单 -->
        <div class="material-first-level material-item">
            <div class="first-item" v-for="(item,index) in material_list" :key="index">
                {{item.label}}
            </div>
        </div>
        <!-- 右侧二级分类 -->
        <div class="material-two-level material-item">
            <div class="two-group">
                <el-collapse accordion v-model="curActive">
                    <el-collapse-item v-for="(item,index) in material_list[0].children" :name="index" :key="index">
                        <template #title>
                            {{item.group}}
                        </template>
                        <div class="group-item-list">
                            <div class="item" v-for="(items,indexs) in item.children" :key="indexs" @click="create_model(items)">
                                <img :src="items.img_url">
                            </div>
                        </div>
                    </el-collapse-item>
                </el-collapse>
            </div>
        </div>
    </div>
</template>

<script>
// FIXME 暂时注释，不适用这种方式
// import bus from '@/common/EventBus';

export default {
    components: {},
    data() {
        return {
            curActive: 0,
            material_list: [
                {
                    label: '室外',
                    children: [
                        {
                            group: '圈地',
                            children: [
                                {
                                    img_url: '/static/img/ground.png',
                                    // model_url: '/static/model/matilda/scene.gltf',
                                    name: '绘制地板',
                                    mode: 'drag_drop', // 执行的方法 --枚举类管理 圈地(drag_drop) 点击摆放(click_display) 绘制围墙(draw_fence) 绘制墙体(draw_wall)
                                },
                                {
                                    img_url: '/static/img/RoomWall.png',
                                    name: '绘制墙体',
                                    mode: 'drag_wall', // 执行的方法 --枚举类管理 圈地(drag_drop) 点击摆放(click_display) 绘制围墙(draw_fence) 绘制墙体(draw_wall)
                                },
                                {
                                    img_url: '/static/img/build_sign.png',
                                    // model_url: '/static/model/matilda/scene.gltf',
                                    name: '建筑',
                                    mode: 'build_sign', // 执行的方法 --枚举类管理 圈地(drag_drop) 点击摆放(click_display) 绘制围墙(draw_fence)
                                },
                            ],
                        },
                        {
                            group: '围墙',
                            children: [
                                {
                                    img_url: '/static/img/fence_01.png',
                                    model_url: '/static/model/fence/fence.fbx',
                                    name: '围栏',
                                    mode: 'draw_fence', // 执行的方法 --枚举类管理 圈地(drag_drop) 点击摆放(click_display) 绘制围墙(draw_fence)
                                },
                            ],
                        },
                        {
                            group: '人物',
                            children: [
                                {
                                    img_url: '/static/img/matilda.png',
                                    model_url: '/static/model/matilda/scene.gltf',
                                    name: '人物',
                                    mode: 'click_display', // 执行的方法 --枚举类管理 圈地(drag_drop) 点击摆放(click_display) 绘制围墙(draw_fence)
                                },
                            ],
                        },
                        {
                            group: '草坪',
                            children: [
                                {
                                    img_url: '/static/img/tree.png',
                                    model_url: '/static/model/grass2/scene.gltf',
                                    name: '草坪',
                                    mode: 'click_display', // 执行的方法 --枚举类管理 圈地(drag_drop) 点击摆放(click_display) 绘制围墙(draw_fence)
                                },
                                {
                                    img_url: '/static/img/tree.png',
                                    model_url: '/static/model/wall/test.gltf',
                                    name: '草坪',
                                    mode: 'click_display', // 执行的方法 --枚举类管理 圈地(drag_drop) 点击摆放(click_display) 绘制围墙(draw_fence)
                                },
                            ],
                        },
                    ],
                },
            ],
        };
    },
    methods: {
        create_model(obj) {
            console.log('开始创建模型');
            wzEditor.create_model(obj);
            // console.log('开始创建模型');
            // console.log(bus);
            // bus.$emit('create_model', obj);
            // evt.dataTransfer.setData('model_info', JSON.stringify(obj));
            // console.log(JSON.parse(evt.dataTransfer.getData('model_info')));
        },
    },
};
</script>
<style lang="scss">
.editor-material {
    .el-collapse{
        --el-collapse-header-background-color: #303131;
        --el-collapse-content-background-color: #303131;
        --el-collapse-header-font-color: white;
        --el-collapse-content-font-color: white;
        --el-collapse-border-color: rgba(151,151,151,0.21);

        border-top: 1px solid rgba(151,151,151,0.21);
        border-bottom: 1px solid rgba(151,151,151,0.21);
    }
}
</style>
<style lang='scss' scoped>
// 物料区
.editor-material{
    display: flex;
    width: 370px;
    justify-content: space-between;
    padding: 5px;
    color: white;
    background: #303131;

    .material-first-level{
        width: 50px;

        .first-item{
            height: 50px;
            margin-bottom: 2px;
            line-height: 50px;
            text-align: center;
            border: 1px solid rgba(151,151,151,0.21);
        }
    }

    .material-two-level {
        width: calc(100% - 62px);

        .two-group{

            .group-item-list{
                display: flex;
                flex-wrap: wrap;
                justify-content: space-between;

                .item{
                    width: 90px;
                    height: 90px;
                    margin-top: 5px;
                    line-height: 90px;
                    text-align: center;
                    cursor: move;
                    border: 1px solid rgba(151,151,151,0.21);

                    img {
                        width: 100%;
                        height: 100%;
                    }
                }
            }
        }
    }
}
</style>
