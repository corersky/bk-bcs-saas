<template src="./tmpl-instantiation.html"></template>

<script>
    import mixinBaseInstantiation from '../mixins/mixin-base-instantiation'

    export default {
        mixins: [mixinBaseInstantiation],
        data () {
            return {
                CATEGORY: 'statefulset'
            }
        },
        methods: {
            /**
             * 返回模板集列表
             *
             * @param {boolean} needConfirm 是否需要 confirm 提示
             */
            goTemplateset (needConfirm) {
                const params = {
                    projectId: this.projectId,
                    projectCode: this.projectCode,
                    tplsetId: this.templateId,
                    searchParamsList: this.searchParamsList
                }
                if (needConfirm) {
                    const me = this
                    const h = me.$createElement
                    me.$bkInfo({
                        title: '',
                        content: h('p', `确定要取消${me.tmplAppName}实例化操作？`),
                        confirmFn () {
                            me.$router.push({
                                name: 'statefulset',
                                params: params
                            })
                        }
                    })
                } else {
                    this.$router.push({
                        name: 'statefulset',
                        params: params
                    })
                }
            }
        }
    }
</script>

<style scoped>
    @import '../instantiation.css';
</style>
