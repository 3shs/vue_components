<template>
    <div>
        <i-form :model="checkForm" :rules="checkFormRules" ref="checkForm">
            <i-form-item label="用户名" prop="name">
                <i-input v-model="checkForm.name" :value="checkForm.name"></i-input>
            </i-form-item>
            <i-form-item label="邮箱" prop="mail">
                <i-input v-model="checkForm.mail"></i-input>
            </i-form-item>
            <button @click="submitForm">提交</button>
            <button @click="resetForm">重置</button>
        </i-form>
    </div>
</template>
<script>
import iForm from '../components/form/form'
import iFormItem from '../components/form/form-item'
import iInput from '../components/input/input'
export default {
    components: {
        iForm,
        iFormItem,
        iInput
    },
    data () {
        return {
            checkForm: {
                name: '',
                mail: ''
            },
            checkFormRules: {
                name: [
                    { required: true, message: '用户名不能为空', trigger: 'blur' }
                ],
                mail: [
                    { required: true, message: '邮箱不能为空', trigger: 'blur' },
                    { type: 'email', message: '邮箱格式不正确', trigger: 'blur' }
                ],
            }
        }
    },
    methods: {
        submitForm () {
            this.$refs.checkForm.validate( valid => {
                if (valid) {
                    window.alert('提交成功')
                } else {
                    window.alert('提交失败')
                }
            })
        },
        resetForm () {

        }
    }
}
</script>
<style lang="less" scoped>

</style>