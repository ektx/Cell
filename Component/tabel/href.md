
# Vue-excel

表格模板

```html
<!-- vue.js template -->
<script type="text/x-template" id="v-table-tem">
    <article>
        <table class="excel-table">
            <thead>
            <tr>
                <th v-for="th in datas.header">
                    {{th}}
                </th>
            </tr>
            </thead>
            <tbody>
            <tr v-for="(trData, index) in datas.data">
                <template v-for="(val, key, i) in trData">
                    <template v-if="key !== 'orgId'">
                        <td>
                            <a :href="trData.orgId">
                            <template v-if="i === 0">{{index+1}}.</template>
                            {{val}}
                            <template v-if="i === Object.keys(trData).length -2 && ('orgId' in trData)"><i>></i></template>
                            </a> 
                        </td>
                    </template>
                </template>
            </tr>
            </tbody>
        </table>
    </article>
</script>


<!-- 2.引用模板 -->
<script>
    // 自定义组件
    Vue.component('vue-excel', {
        template: '#v-table-tem',
        props: [ 'datas' ]
    });
</script>

<!-- 3.使用 -->
<vue-excel v-bind:datas="your-data"></vue-excel>

```