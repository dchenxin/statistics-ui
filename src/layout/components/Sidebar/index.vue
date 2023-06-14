<template>
    <div :class="{'has-logo':showLogo}">
        <logo v-if="showLogo" :collapse="isCollapse" />
        <el-scrollbar wrap-class="scrollbar-wrapper">
            <el-menu
                :default-active="activeMenu"
                :collapse="isCollapse"
                :background-color="variables.menuBg"
                :text-color="variables.menuText"
                :unique-opened="true"
                :active-text-color="settings.theme"
                :collapse-transition="false"
                mode="vertical"
            >
                <sidebar-item
                    v-for="(route, index) in permission_routes"
                    :key="route.path  + index"
                    :item="route"
                    :base-path="route.path"
                />
            </el-menu>
        </el-scrollbar>
    </div>
</template>

<script>
import { mapGetters, mapState } from "vuex";
import Logo from "./Logo";
import SidebarItem from "./SidebarItem";
import variables from "@/assets/styles/variables.scss";

export default {
    components: { SidebarItem, Logo },
    computed: {
        ...mapState(["settings"]),
        ...mapGetters(["permission_routes", "sidebar"]),
        activeMenu() {
            const route = this.$route;
            const { meta, path } = route;
            // if set path, the sidebar will highlight the path you set
            if (meta.activeMenu) {
                return meta.activeMenu;
            }

          // 前端大屏新窗口 跳转
          if (path.includes('statistics')) {
            let routes;
            if (path.includes('passengerFlow')) {
               routes = this.$router.resolve({ name: 'passengerFlowStatistics' })
            }else if(path.includes('energyConsumption')){
               routes = this.$router.resolve({ name: 'energyConsumptionStatistics' })
            }else if(path.includes('operations')){
               routes = this.$router.resolve({ name: 'operationsStatistics' })
            }else if(path.includes('secure')){
               routes = this.$router.resolve({ name: 'secureStatistics' })
            }
            //新窗口打开页面
            window.open(routes.href, '_blank')
            //原窗口保持原来的页面
            this.$router.go(-1);
            return 0;
          }
            return path;
        },
        showLogo() {
            return this.$store.state.settings.sidebarLogo;
        },
        variables() {
            return variables;
        },
        isCollapse() {
            return !this.sidebar.opened;
        }
    }
};
</script>
