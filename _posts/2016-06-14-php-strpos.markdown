---
layout: post
title:  "PHP strpos函数的应用"
date:   2015-06-14 11:43:59
author: Hoodps
categories: PHP
---

在PHP中经常用到字符串的查找函数`strpos()`,已判读某个字符串是否在另外一个字符串中,同是还可以判读字符串中的出现的位置。
    是否区分大小写等等。

## 在权限控制中应用
    
    /**
     * 判断管理员对某一个操作是否有权限。
     *
     * 根据当前对应的action_code，然后再和用户session里面的action_list做匹配，
     * 以此来决定是否可以继续执行。
     * @param     string    $priv_str    操作对应的priv_str
     * @param     string    $msg_type       返回的类型
     * @return true/false
     */
    function admin_priv($priv_str, $msg_type = '' , $msg_output = true)
    {
        global $_LANG;

        if ($_SESSION['action_list'] == 'all')
        {
            return true;
        }

        if (strpos(',' . $_SESSION['action_list'] . ',', ',' . $priv_str . ',') 
        === false)
        {
            $link[] = array('text' => $_LANG['go_back'], 
                            'href' => 'javascript:history.back(-1)'
                            );
            if ( $msg_output)
            {
                sys_msg($_LANG['priv_error'], 0, $link);
            }
            return false;
        }
        else
        {
            return true;
        }
    }

用户的权限都存在session里面的action_list字段中，例如

["action_list"]=> string(264) "goods_manage,remove_back,cat_manage,
    cat_drop,attr_manage,brand_manage,comment_priv,tag_manage,goods_type,
    goods_auto,virualcard,picture_batch,goods_export,goods_batch,
    gen_goods_script,article_cat,article_manage,shopinfo_manage,
    shophelp_manage,vote_priv,article_auto" 
每一个控制器用逗号隔开,然后使用strpos()函数查找字符串第一次出现的位置。

相关函数：

 - stripos()- 查找字符串在另一字符串中第一次出现的位置（不区分大小写）
 - strripos()- 查找字符串在另一字符串中最后一次出现的位置（不区分大小写）
 - strrpos()- 查找字符串在另一字符串中最后一次出现的位置（区分大小写）




