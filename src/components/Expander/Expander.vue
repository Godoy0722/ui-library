<template>
	<button class="expander" @click="$emit('toggle')">
		<Icon v-if="isExpanded" icon="ChevronUp" class="h-5 w-5" :inline="true" />
		<Icon v-else icon="ChevronDown" class="h-5 w-5" :inline="true" />
		<span v-if="isExpanded" class="-screenReader">
			{{ t('list.viewLess', {name: itemName}) }}
		</span>
		<span v-else class="-screenReader">
			{{ t('list.viewMore', {name: itemName}) }}
		</span>
	</button>
</template>

<script>
import Icon from '@/components/Icon/Icon.vue';

export default {
	components: {Icon},
	props: {
		isExpanded: {
			type: Boolean,
			default() {
				return false;
			},
		},
		itemName: {
			type: String,
			required: true,
		},
	},
};
</script>

<style lang="less">
@import '../../styles/_import';

.expander {
	padding: 0 0.5em;
	background: transparent;
	border: @bg-border-light;
	border-radius: @radius;
	font-size: @font-sml;
	line-height: 2rem;
	color: @primary;
	box-shadow: 0 1px 0 @bg-border-color-light;
	cursor: pointer;

	&:hover,
	&:focus {
		color: @primary;
		border-color: @primary;
		outline: 0;
	}

	&:active {
		box-shadow: 0 0 2px;
	}
}
</style>
