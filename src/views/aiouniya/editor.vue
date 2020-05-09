//GENERATE_START
<template>
	<el-dialog :title="title" :visible.sync="visible">
		<el-form v-if="visible == true" ref="saveForm" :model="entity" :rules="rules" status-icon label-width="120px">
			<el-form-item :label="$t('aiouniya.qmdj')">
			   <el-input v-if="!''" v-model.trim="entity.qmdj"></el-input>
			</el-form-item>
			<el-form-item :label="$t('aiouniya.abab')">
			   <el-input v-if="!''" v-model.trim="entity.abab"></el-input>
			</el-form-item>
			<el-form-item :label="$t('aiouniya.aabb')">
			   <el-input v-if="!''" v-model.trim="entity.aabb"></el-input>
			</el-form-item>
		</el-form>
	    <span slot="footer" class="dialog-footer">
	      	<el-button @click="visible = false">{{$t('actions.cancel')}}</el-button>
	      	<el-button type="primary" @click="onOK">{{$t('actions.ok')}}</el-button>
	    </span>
	</el-dialog>
</template>
<script>
	import { getJson }  from '@/utils/restapi'
	import { numberInput,numberSpotInput,notChinese} from '@/utils/validate'
	export default {
		name: 'ClsTestEditor',
		data() {
			return {
				title : 'Untitled',
				visible: false,
				entity: {},
				mode : null,
				chaincodeOptions: [],
				rules: {		 
                }
			}
		},
		mounted(){
			// Do nothing
		},
		methods:{
			open(entity){
				this.visible = true
				this.entity = entity
				if(this.entity.null){
					this.mode = 'EDIT'
					this.title = this.$t('aiouniya.edit')
				}else{
					this.mode = 'NEW'
					this.title = this.$t('aiouniya.addnew')
				}
			},
			getMode(){
				return this.mode
			},
			getEntity(){
				return this.entity
			},
			close(){
				this.visible = false
			},
			onOK(){
				this.$emit("onOK", this.entity)
			}
		}
	}
</script>
//GENERATE_END