
# 项目介绍

Java项目 智能养生平台
使用技术：spring+mybatis+springmvc+html+JavaScript+css+layui+jQuery
运行环境
jdk8+mysql+IntelliJ IDEA+maven
主要分两个端，用户端和管理员端
网站功能：实现论坛帖子管理，论坛帖子分类管理，留言管理，用户登录注册，管理员管理，
验证码使用，ajax使用，分页查询，报表统计，友情链接，问卷提交，问卷添加修改，问卷结果查看等。
管理员端主要功能:
管理员管理、用户管理、问卷管理、问卷结果管理、帖子分类管理、数据分析统计、公告管理、帖子管理、友情链接管理、留言管理



# 环境要求

1.运行环境：最好是java jdk1.8,我们在这个平台上运行的。其他版本理论上也可以。 

2.IDE环境：IDEA,Eclipse,Myeclipse都可以。推荐IDEA; 

3.tomcat环境：Tomcat7.x,8.X,9.x版本均可 

4.硬件环境：windows7/8/10 4G内存以上；或者Mac OS; 

5.是否Maven项目：是；查看源码目录中是否包含pom.xml;若包含，则为maven项目，否则为非maven.项目 

6.数据库：MySql5.7/8.0等版本均可；

# 技术栈

后台框架：Spring Boot、MyBatis

数据库：MySQL

环境：JDK8、TOMCAT、IDEA

# 使用说明

1.使用Navicati或者其它工具，在mysql中创建对应sq文件名称的数据库，并导入项目的sql文件； 

2.使用IDEA/Eclipse/MyEclipse导入项目，修改配置，运行项目； 

3.将项目中config-propertiesi配置文件中的数据库配置改为自己的配置，然后运行；

# 运行指导

idea导入源码空间站顶目教程说明(Vindows版)-ssm篇：

http://mtw.so/5MHvZq

源码地址：[http://codegym.top](http://codegym.top/)。 


# 运行截图

## 页面

![QQ浏览器截图20231231005343](https://github.com/catnipculture/smarthealth/assets/126983311/c31d8f1d-4308-4d2c-9a4c-08b1736295f2)
![QQ浏览器截图20231231004809](https://github.com/catnipculture/smarthealth/assets/126983311/e5a4d37f-d431-4d25-affe-981b68038b00)
![QQ浏览器截图20231231004800](https://github.com/catnipculture/smarthealth/assets/126983311/eb6e839c-4962-4107-b56f-2712f9b4d73e)
![QQ浏览器截图20231231004752](https://github.com/catnipculture/smarthealth/assets/126983311/b42b90ce-ce18-451e-ab90-e90cd1519f0e)
![QQ浏览器截图20231231004743](https://github.com/catnipculture/smarthealth/assets/126983311/91aa7026-3f48-437a-bb41-1a1b94a28ef5)
![QQ浏览器截图20231231004733](https://github.com/catnipculture/smarthealth/assets/126983311/86a9b49b-fae9-426b-b7ef-ccfeb4c7b5f3)
![QQ浏览器截图20231231004725](https://github.com/catnipculture/smarthealth/assets/126983311/b1309aa1-e3c6-4a37-b467-9cb836bbe3bc)
![QQ浏览器截图20231231004716](https://github.com/catnipculture/smarthealth/assets/126983311/080c52f2-8b7d-4ac1-8729-dd58188be47c)
![QQ浏览器截图20231231004658](https://github.com/catnipculture/smarthealth/assets/126983311/0721a9a3-18c6-48d8-ad1f-82720dc80e69)
![QQ浏览器截图20231231004644](https://github.com/catnipculture/smarthealth/assets/126983311/574980e8-95e9-4e0e-93ae-811c98c91bcd)
![QQ浏览器截图20231231004629](https://github.com/catnipculture/smarthealth/assets/126983311/95d798dc-58ab-4d36-8fd4-57a57caf821b)
![QQ浏览器截图20231231004616](https://github.com/catnipculture/smarthealth/assets/126983311/7af8c24e-35b2-497a-8be8-71eb2889eed4)
![QQ浏览器截图20231231004605](https://github.com/catnipculture/smarthealth/assets/126983311/6c72a1da-52a3-463c-b3d4-5185449b8d61)
![QQ浏览器截图20231231004551](https://github.com/catnipculture/smarthealth/assets/126983311/0b6833e3-7529-4d29-a329-2165db537be1)
![QQ浏览器截图20231231003811](https://github.com/catnipculture/smarthealth/assets/126983311/3a8fdd17-0d39-4faa-85ea-050a5d2b27ed)


### 相关代码

AdminController

```java
package com.module.controller.base;

import com.module.mapper.AdminMapper;
import com.module.pojo.Admin;
import com.module.util.MD5Util;
import com.module.util.ResultUtil;
import com.github.pagehelper.PageHelper;
import com.github.pagehelper.PageInfo;
import org.apache.commons.lang.StringUtils;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.ResponseBody;

import javax.servlet.http.HttpSession;
import java.util.Date;
import java.util.HashMap;
import java.util.List;
import java.util.Map;

/**
 * 页面请求控制  管理员管理
 */
@Controller
public class AdminController {
    @Autowired
    AdminMapper adminMapper;

    /**
     * 跳转到列表页面
     *
     * @return
     */
    @RequestMapping("manage/adminList")
    public String adminList() {
        return "manage/admin/adminList";
    }

    /**
     * 跳转到添加页面
     *
     * @return
     */
    @RequestMapping("manage/addAdmin")
    public String addAdmin(Model model) {
        return "manage/admin/saveAdmin";
    }

    /**
     * 跳转到修改页面
     *
     * @param id
     * @param model
     * @return
     */
    @RequestMapping("manage/editAdmin")
    public String editAdmin(Integer id, Model model) {
        Admin admin = adminMapper.selectAdminById(id);
        model.addAttribute("admin", admin);
        return "manage/admin/saveAdmin";
    }

    /**
     * 分页查询
     *
     * @param page  默认第一页
     * @param limit 默认每页显示10条
     * @return
     */
    @RequestMapping("manage/queryAdminList")
    @ResponseBody
    public ResultUtil getCarouseList(Integer page, Integer limit, String keyword) {
        if (null == page) { //默认第一页
            page = 1;
        }
        if (null == limit) { //默认每页10条
            limit = 10;
        }
        Map map = new HashMap();
        if (StringUtils.isNotEmpty(keyword)) {
            map.put("keyword", keyword);
        }
        PageHelper.startPage(page, limit, true);
        List<Admin> list = adminMapper.selectAll(map);
        PageInfo<Admin> pageInfo = new PageInfo<Admin>(list);  //使用mybatis分页插件
        ResultUtil resultUtil = new ResultUtil();
        resultUtil.setCode(0);  //设置返回状态0为成功
        resultUtil.setCount(pageInfo.getTotal());  //获取总记录数目 类似count(*)
        resultUtil.setData(pageInfo.getList());    //获取当前查询出来的集合
        return resultUtil;
    }

    /**
     * 插入记录
     */
    @RequestMapping("manage/saveAdmin")
    @ResponseBody
    public ResultUtil saveAdmin(Admin admin, HttpSession session) {
        Date nowTime = new Date();
        admin.setCreatetime(nowTime);
        admin.setAdminpassword(MD5Util.getMd5(admin.getAdminpassword())); //加密密码
        try {
            adminMapper.insertAdmin(admin);
            return ResultUtil.ok("添加管理员成功");
        } catch (Exception e) {
            return ResultUtil.error("添加管理员出错,稍后再试！");
        }
    }

    /**
     * 更新记录
     */
    @RequestMapping("manage/updateAdmin")
    @ResponseBody
    public ResultUtil updateAdmin(Admin admin, HttpSession session) {
        Date nowTime = new Date();
        admin.setCreatetime(nowTime);
        admin.setAdminpassword(MD5Util.getMd5(admin.getAdminpassword())); //加密密码
        try {
            adminMapper.updateAdmin(admin);
            return ResultUtil.ok("修改管理员成功");
        } catch (Exception e) {
            return ResultUtil.error("修改管理员出错,稍后再试！");
        }
    }


    /**
     * 根据ID删除
     *
     * @param id
     * @return
     */
    @RequestMapping("manage/deleteAdmin")
    @ResponseBody
    public ResultUtil deleteAdminById(Integer id) {
        try {
            adminMapper.deleteAdminById(id);
            return ResultUtil.ok("删除管理员成功");
        } catch (Exception e) {
            return ResultUtil.error("删除管理员出错,稍后再试！");
        }
    }

    /**
     * 根据ID批量删除
     *
     * @param idsStr
     * @return
     */
    @RequestMapping("manage/deletesAdmin")
    @ResponseBody
    public ResultUtil deletesAdmin(String idsStr) {
        try {
            if (!StringUtils.isBlank(idsStr)) {
                String[] ids = idsStr.split(",");
                for (String id : ids) {
                    adminMapper.deleteAdminById(Integer.parseInt(id));
                }
            }
            return ResultUtil.ok("批量删除管理员成功");
        } catch (Exception e) {
            return ResultUtil.error("删除管理员出错,稍后再试！");
        }
    }


}
```



BaseController


```java
package com.module.controller.base;

import com.github.pagehelper.Page;
import org.springframework.beans.propertyeditors.CustomDateEditor;
import org.springframework.ui.Model;
import org.springframework.web.bind.WebDataBinder;
import org.springframework.web.bind.annotation.InitBinder;

import java.text.SimpleDateFormat;
import java.util.Date;

/**
 * 所有控制器的父类
 */
public class BaseController {

    /**
     * 时间转换处理器
     *
     * @param binder
     */
    @InitBinder
    protected void initBinder(WebDataBinder binder) {
        binder.registerCustomEditor(
                Date.class,
                new CustomDateEditor(
                        new SimpleDateFormat("yyyy-MM-dd HH:mm:ss"),
                        true    //true:允许输入空值，false:不能为空值
                )
        );
    }


    /**
     * 分页参数方法封装
     *
     * @param model
     * @param pathURL  分页地址
     * @param pageInfo 分页查询信息
     */
    public static void setPageParams(Model model, String pathURL, Page<Object> pageInfo) {
        model.addAttribute("currentPage", pageInfo.getPageNum()); //绑定当前页参数
        model.addAttribute("totalPage", pageInfo.getPages()); //绑定总页数
        model.addAttribute("totalNums", pageInfo.getTotal()); //绑定总记录条数
        model.addAttribute("pathURL", pathURL); //绑定分页跳转地址
    }


}
```
