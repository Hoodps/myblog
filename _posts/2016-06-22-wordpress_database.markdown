---
layout: post
title:  "github 优秀Python项目4"
date:   2015-06-22 15:43:59
author: Hoodps
categories: php
---

wordpress 数据库

## 数据字典

	DROP TABLE IF EXISTS `wp_commentmeta`;
	CREATE TABLE `wp_commentmeta` (
	  `meta_id` bigint(20) unsigned NOT NULL AUTO_INCREMENT,
	  `comment_id` bigint(20) unsigned NOT NULL DEFAULT '0',
	  `meta_key` varchar(255) COLLATE utf8mb4_unicode_ci DEFAULT NULL,
	  `meta_value` longtext COLLATE utf8mb4_unicode_ci,
	  PRIMARY KEY (`meta_id`),
	  KEY `comment_id` (`comment_id`),
	  KEY `meta_key` (`meta_key`(191))
	) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

	-- ----------------------------
	--  Table structure for `wp_comments`
	-- ----------------------------
	DROP TABLE IF EXISTS `wp_comments`;
	CREATE TABLE `wp_comments` (
	  `comment_ID` bigint(20) unsigned NOT NULL AUTO_INCREMENT,
	  `comment_post_ID` bigint(20) unsigned NOT NULL DEFAULT '0',
	  `comment_author` tinytext COLLATE utf8mb4_unicode_ci NOT NULL,
	  `comment_author_email` varchar(100) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '',
	  `comment_author_url` varchar(200) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '',
	  `comment_author_IP` varchar(100) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '',
	  `comment_date` datetime NOT NULL DEFAULT '0000-00-00 00:00:00',
	  `comment_date_gmt` datetime NOT NULL DEFAULT '0000-00-00 00:00:00',
	  `comment_content` text COLLATE utf8mb4_unicode_ci NOT NULL,
	  `comment_karma` int(11) NOT NULL DEFAULT '0',
	  `comment_approved` varchar(20) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '1',
	  `comment_agent` varchar(255) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '',
	  `comment_type` varchar(20) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '',
	  `comment_parent` bigint(20) unsigned NOT NULL DEFAULT '0',
	  `user_id` bigint(20) unsigned NOT NULL DEFAULT '0',
	  PRIMARY KEY (`comment_ID`),
	  KEY `comment_post_ID` (`comment_post_ID`),
	  KEY `comment_approved_date_gmt` (`comment_approved`,`comment_date_gmt`),
	  KEY `comment_date_gmt` (`comment_date_gmt`),
	  KEY `comment_parent` (`comment_parent`),
	  KEY `comment_author_email` (`comment_author_email`(10))
	) ENGINE=InnoDB AUTO_INCREMENT=2 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

	-- ----------------------------
	--  Records of `wp_comments`
	-- ----------------------------
	BEGIN;
	INSERT INTO `wp_comments` VALUES ('1', '1', 'WordPress先生', '', 'https://wordpress.org/', '', '2015-12-03 21:42:06', '2015-12-03 13:42:06', '您好，这是一条评论。\n要删除评论，请先登录，然后再查看这篇文章的评论。登录后您可以看到编辑或者删除评论的选项。', '0', '1', '', '', '0', '0');
	COMMIT;

	-- ----------------------------
	--  Table structure for `wp_form`
	-- ----------------------------
	DROP TABLE IF EXISTS `wp_form`;
	CREATE TABLE `wp_form` (
	  `id` smallint(4) unsigned NOT NULL AUTO_INCREMENT,
	  `title` varchar(255) NOT NULL,
	  `content` varchar(255) NOT NULL,
	  `create_time` int(11) unsigned NOT NULL,
	  PRIMARY KEY (`id`)
	) ENGINE=MyISAM AUTO_INCREMENT=29 DEFAULT CHARSET=utf8;

	-- ----------------------------
	--  Records of `wp_form`
	-- ----------------------------
	BEGIN;
	INSERT INTO `wp_form` VALUES ('1', 'rwr', 'wrwrqsd', '1449238100'), ('2', 'sdafhreu', 'afnjkkjhf', '1449238119'), ('3', 'test', 'safsddsfafdf', '345678'), ('4', 'test', 'safsddsfafdf', '345678'), ('5', 'test', 'safsddsfafdf', '345678'), ('6', 'test', 'safsddsfafdf', '345678'), ('7', 'test', 'safsddsfafdf', '345678'), ('8', 'test', 'safsddsfafdf', '345678'), ('9', 'test', 'safsddsfafdf', '345678'), ('10', 'test', 'safsddsfafdf', '345678'), ('11', 'test', 'safsddsfafdf', '345678'), ('12', 'test', 'safsddsfafdf', '345678'), ('13', 'test', 'safsddsfafdf', '345678'), ('14', 'test', 'safsddsfafdf', '345678'), ('15', 'test', 'safsddsfafdf', '345678'), ('16', 'test', 'safsddsfafdf', '345678'), ('17', 'test', 'safsddsfafdf', '345678'), ('18', 'test', 'safsddsfafdf', '345678'), ('19', 'test', 'safsddsfafdf', '345678'), ('20', 'test', 'safsddsfafdf', '345678'), ('21', 'test', 'safsddsfafdf', '345678'), ('22', 'test', 'safsddsfafdf', '345678'), ('23', 'test', 'safsddsfafdf', '1449240503'), ('24', 'test', 'safsddsfafdf', '1449240504'), ('25', 'test', 'safsddsfafdf', '1449240505'), ('26', 'test', 'safsddsfafdf', '1449240506'), ('27', 'test', 'safsddsfafdf', '1449240507'), ('28', 'hhj', 'huuh', '1449240600');
	COMMIT;

	-- ----------------------------
	--  Table structure for `wp_links`
	-- ----------------------------
	DROP TABLE IF EXISTS `wp_links`;
	CREATE TABLE `wp_links` (
	  `link_id` bigint(20) unsigned NOT NULL AUTO_INCREMENT,
	  `link_url` varchar(255) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '',
	  `link_name` varchar(255) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '',
	  `link_image` varchar(255) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '',
	  `link_target` varchar(25) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '',
	  `link_description` varchar(255) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '',
	  `link_visible` varchar(20) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT 'Y',
	  `link_owner` bigint(20) unsigned NOT NULL DEFAULT '1',
	  `link_rating` int(11) NOT NULL DEFAULT '0',
	  `link_updated` datetime NOT NULL DEFAULT '0000-00-00 00:00:00',
	  `link_rel` varchar(255) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '',
	  `link_notes` mediumtext COLLATE utf8mb4_unicode_ci NOT NULL,
	  `link_rss` varchar(255) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '',
	  PRIMARY KEY (`link_id`),
	  KEY `link_visible` (`link_visible`)
	) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

	-- ----------------------------
	--  Table structure for `wp_options`
	-- ----------------------------
	DROP TABLE IF EXISTS `wp_options`;
	CREATE TABLE `wp_options` (
	  `option_id` bigint(20) unsigned NOT NULL AUTO_INCREMENT,
	  `option_name` varchar(64) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '',
	  `option_value` longtext COLLATE utf8mb4_unicode_ci NOT NULL,
	  `autoload` varchar(20) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT 'yes',
	  PRIMARY KEY (`option_id`),
	  UNIQUE KEY `option_name` (`option_name`)
	) ENGINE=InnoDB AUTO_INCREMENT=187 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

	-- ----------------------------
	--  Records of `wp_options`
	-- ----------------------------
	BEGIN;
	INSERT INTO `wp_options` VALUES ('1', 'siteurl', 'http://mysites/wordpress', 'yes'), ('2', 'home', 'http://mysites/wordpress', 'yes'), ('3', 'blogname', '我的博客', 'yes'), ('4', 'blogdescription', '又一个WordPress站点', 'yes'), ('5', 'users_can_register', '0', 'yes'), ('6', 'admin_email', 'admin@qq.com', 'yes'), ('7', 'start_of_week', '1', 'yes'), ('8', 'use_balanceTags', '0', 'yes'), ('9', 'use_smilies', '1', 'yes'), ('10', 'require_name_email', '1', 'yes'), ('11', 'comments_notify', '1', 'yes'), ('12', 'posts_per_rss', '10', 'yes'), ('13', 'rss_use_excerpt', '0', 'yes'), ('14', 'mailserver_url', 'mail.example.com', 'yes'), ('15', 'mailserver_login', 'login@example.com', 'yes'), ('16', 'mailserver_pass', 'password', 'yes'), ('17', 'mailserver_port', '110', 'yes'), ('18', 'default_category', '1', 'yes'), ('19', 'default_comment_status', 'open', 'yes'), ('20', 'default_ping_status', 'open', 'yes'), ('21', 'default_pingback_flag', '0', 'yes'), ('22', 'posts_per_page', '10', 'yes'), ('23', 'date_format', 'Y年n月j日', 'yes'), ('24', 'time_format', 'ag:i', 'yes'), ('25', 'links_updated_date_format', 'Y年n月j日ag:i', 'yes'), ('26', 'comment_moderation', '0', 'yes'), ('27', 'moderation_notify', '1', 'yes'), ('28', 'permalink_structure', '/index.php/%year%/%monthnum%/%day%/%postname%/', 'yes'), ('29', 'gzipcompression', '0', 'yes'), ('30', 'hack_file', '0', 'yes'), ('31', 'blog_charset', 'UTF-8', 'yes'), ('32', 'moderation_keys', '', 'no'), ('33', 'active_plugins', 'a:0:{}', 'yes'), ('34', 'category_base', '', 'yes'), ('35', 'ping_sites', 'http://rpc.pingomatic.com/', 'yes'), ('36', 'advanced_edit', '0', 'yes'), ('37', 'comment_max_links', '2', 'yes'), ('38', 'gmt_offset', '0', 'yes'), ('39', 'default_email_category', '1', 'yes'), ('40', 'recently_edited', '', 'no'), ('41', 'template', 'twentyfifteen', 'yes'), ('42', 'stylesheet', 'twentyfifteen', 'yes'), ('43', 'comment_whitelist', '1', 'yes'), ('44', 'blacklist_keys', '', 'no'), ('45', 'comment_registration', '0', 'yes'), ('46', 'html_type', 'text/html', 'yes'), ('47', 'use_trackback', '0', 'yes'), ('48', 'default_role', 'subscriber', 'yes'), ('49', 'db_version', '33056', 'yes'), ('50', 'uploads_use_yearmonth_folders', '1', 'yes'), ('51', 'upload_path', '', 'yes'), ('52', 'blog_public', '0', 'yes'), ('53', 'default_link_category', '2', 'yes'), ('54', 'show_on_front', 'posts', 'yes'), ('55', 'tag_base', '', 'yes'), ('56', 'show_avatars', '1', 'yes'), ('57', 'avatar_rating', 'G', 'yes'), ('58', 'upload_url_path', '', 'yes'), ('59', 'thumbnail_size_w', '150', 'yes'), ('60', 'thumbnail_size_h', '150', 'yes'), ('61', 'thumbnail_crop', '1', 'yes'), ('62', 'medium_size_w', '300', 'yes'), ('63', 'medium_size_h', '300', 'yes'), ('64', 'avatar_default', 'mystery', 'yes'), ('65', 'large_size_w', '1024', 'yes'), ('66', 'large_size_h', '1024', 'yes'), ('67', 'image_default_link_type', 'file', 'yes'), ('68', 'image_default_size', '', 'yes'), ('69', 'image_default_align', '', 'yes'), ('70', 'close_comments_for_old_posts', '0', 'yes'), ('71', 'close_comments_days_old', '14', 'yes'), ('72', 'thread_comments', '1', 'yes'), ('73', 'thread_comments_depth', '5', 'yes'), ('74', 'page_comments', '0', 'yes'), ('75', 'comments_per_page', '50', 'yes'), ('76', 'default_comments_page', 'newest', 'yes'), ('77', 'comment_order', 'asc', 'yes'), ('78', 'sticky_posts', 'a:0:{}', 'yes'), ('79', 'widget_categories', 'a:2:{i:2;a:4:{s:5:\"title\";s:0:\"\";s:5:\"count\";i:0;s:12:\"hierarchical\";i:0;s:8:\"dropdown\";i:0;}s:12:\"_multiwidget\";i:1;}', 'yes'), ('80', 'widget_text', 'a:0:{}', 'yes'), ('81', 'widget_rss', 'a:0:{}', 'yes'), ('82', 'uninstall_plugins', 'a:0:{}', 'no'), ('83', 'timezone_string', 'Asia/Shanghai', 'yes'), ('84', 'page_for_posts', '0', 'yes'), ('85', 'page_on_front', '0', 'yes'), ('86', 'default_post_format', '0', 'yes'), ('87', 'link_manager_enabled', '0', 'yes'), ('88', 'finished_splitting_shared_terms', '1', 'yes'), ('89', 'initial_db_version', '33056', 'yes'), ('90', 'wp_user_roles', 'a:5:{s:13:\"administrator\";a:2:{s:4:\"name\";s:13:\"Administrator\";s:12:\"capabilities\";a:62:{s:13:\"switch_themes\";b:1;s:11:\"edit_themes\";b:1;s:16:\"activate_plugins\";b:1;s:12:\"edit_plugins\";b:1;s:10:\"edit_users\";b:1;s:10:\"edit_files\";b:1;s:14:\"manage_options\";b:1;s:17:\"moderate_comments\";b:1;s:17:\"manage_categories\";b:1;s:12:\"manage_links\";b:1;s:12:\"upload_files\";b:1;s:6:\"import\";b:1;s:15:\"unfiltered_html\";b:1;s:10:\"edit_posts\";b:1;s:17:\"edit_others_posts\";b:1;s:20:\"edit_published_posts\";b:1;s:13:\"publish_posts\";b:1;s:10:\"edit_pages\";b:1;s:4:\"read\";b:1;s:8:\"level_10\";b:1;s:7:\"level_9\";b:1;s:7:\"level_8\";b:1;s:7:\"level_7\";b:1;s:7:\"level_6\";b:1;s:7:\"level_5\";b:1;s:7:\"level_4\";b:1;s:7:\"level_3\";b:1;s:7:\"level_2\";b:1;s:7:\"level_1\";b:1;s:7:\"level_0\";b:1;s:17:\"edit_others_pages\";b:1;s:20:\"edit_published_pages\";b:1;s:13:\"publish_pages\";b:1;s:12:\"delete_pages\";b:1;s:19:\"delete_others_pages\";b:1;s:22:\"delete_published_pages\";b:1;s:12:\"delete_posts\";b:1;s:19:\"delete_others_posts\";b:1;s:22:\"delete_published_posts\";b:1;s:20:\"delete_private_posts\";b:1;s:18:\"edit_private_posts\";b:1;s:18:\"read_private_posts\";b:1;s:20:\"delete_private_pages\";b:1;s:18:\"edit_private_pages\";b:1;s:18:\"read_private_pages\";b:1;s:12:\"delete_users\";b:1;s:12:\"create_users\";b:1;s:17:\"unfiltered_upload\";b:1;s:14:\"edit_dashboard\";b:1;s:14:\"update_plugins\";b:1;s:14:\"delete_plugins\";b:1;s:15:\"install_plugins\";b:1;s:13:\"update_themes\";b:1;s:14:\"install_themes\";b:1;s:11:\"update_core\";b:1;s:10:\"list_users\";b:1;s:12:\"remove_users\";b:1;s:9:\"add_users\";b:1;s:13:\"promote_users\";b:1;s:18:\"edit_theme_options\";b:1;s:13:\"delete_themes\";b:1;s:6:\"export\";b:1;}}s:6:\"editor\";a:2:{s:4:\"name\";s:6:\"Editor\";s:12:\"capabilities\";a:34:{s:17:\"moderate_comments\";b:1;s:17:\"manage_categories\";b:1;s:12:\"manage_links\";b:1;s:12:\"upload_files\";b:1;s:15:\"unfiltered_html\";b:1;s:10:\"edit_posts\";b:1;s:17:\"edit_others_posts\";b:1;s:20:\"edit_published_posts\";b:1;s:13:\"publish_posts\";b:1;s:10:\"edit_pages\";b:1;s:4:\"read\";b:1;s:7:\"level_7\";b:1;s:7:\"level_6\";b:1;s:7:\"level_5\";b:1;s:7:\"level_4\";b:1;s:7:\"level_3\";b:1;s:7:\"level_2\";b:1;s:7:\"level_1\";b:1;s:7:\"level_0\";b:1;s:17:\"edit_others_pages\";b:1;s:20:\"edit_published_pages\";b:1;s:13:\"publish_pages\";b:1;s:12:\"delete_pages\";b:1;s:19:\"delete_others_pages\";b:1;s:22:\"delete_published_pages\";b:1;s:12:\"delete_posts\";b:1;s:19:\"delete_others_posts\";b:1;s:22:\"delete_published_posts\";b:1;s:20:\"delete_private_posts\";b:1;s:18:\"edit_private_posts\";b:1;s:18:\"read_private_posts\";b:1;s:20:\"delete_private_pages\";b:1;s:18:\"edit_private_pages\";b:1;s:18:\"read_private_pages\";b:1;}}s:6:\"author\";a:2:{s:4:\"name\";s:6:\"Author\";s:12:\"capabilities\";a:10:{s:12:\"upload_files\";b:1;s:10:\"edit_posts\";b:1;s:20:\"edit_published_posts\";b:1;s:13:\"publish_posts\";b:1;s:4:\"read\";b:1;s:7:\"level_2\";b:1;s:7:\"level_1\";b:1;s:7:\"level_0\";b:1;s:12:\"delete_posts\";b:1;s:22:\"delete_published_posts\";b:1;}}s:11:\"contributor\";a:2:{s:4:\"name\";s:11:\"Contributor\";s:12:\"capabilities\";a:5:{s:10:\"edit_posts\";b:1;s:4:\"read\";b:1;s:7:\"level_1\";b:1;s:7:\"level_0\";b:1;s:12:\"delete_posts\";b:1;}}s:10:\"subscriber\";a:2:{s:4:\"name\";s:10:\"Subscriber\";s:12:\"capabilities\";a:2:{s:4:\"read\";b:1;s:7:\"level_0\";b:1;}}}', 'yes'), ('91', 'WPLANG', 'zh_CN', 'yes'), ('92', 'widget_search', 'a:2:{i:2;a:1:{s:5:\"title\";s:0:\"\";}s:12:\"_multiwidget\";i:1;}', 'yes'), ('93', 'widget_recent-posts', 'a:2:{i:2;a:2:{s:5:\"title\";s:0:\"\";s:6:\"number\";i:5;}s:12:\"_multiwidget\";i:1;}', 'yes'), ('94', 'widget_recent-comments', 'a:2:{i:2;a:2:{s:5:\"title\";s:0:\"\";s:6:\"number\";i:5;}s:12:\"_multiwidget\";i:1;}', 'yes'), ('95', 'widget_archives', 'a:2:{i:2;a:3:{s:5:\"title\";s:0:\"\";s:5:\"count\";i:0;s:8:\"dropdown\";i:0;}s:12:\"_multiwidget\";i:1;}', 'yes'), ('96', 'widget_meta', 'a:2:{i:2;a:1:{s:5:\"title\";s:0:\"\";}s:12:\"_multiwidget\";i:1;}', 'yes'), ('97', 'sidebars_widgets', 'a:3:{s:19:\"wp_inactive_widgets\";a:0:{}s:9:\"sidebar-1\";a:6:{i:0;s:8:\"search-2\";i:1;s:14:\"recent-posts-2\";i:2;s:17:\"recent-comments-2\";i:3;s:10:\"archives-2\";i:4;s:12:\"categories-2\";i:5;s:6:\"meta-2\";}s:13:\"array_version\";i:3;}', 'yes'), ('100', 'cron', 'a:5:{i:1454134357;a:1:{s:19:\"wp_scheduled_delete\";a:1:{s:32:\"40cd750bba9870f18aada2478b24840a\";a:3:{s:8:\"schedule\";s:5:\"daily\";s:4:\"args\";a:0:{}s:8:\"interval\";i:86400;}}}i:1454135131;a:1:{s:30:\"wp_scheduled_auto_draft_delete\";a:1:{s:32:\"40cd750bba9870f18aada2478b24840a\";a:3:{s:8:\"schedule\";s:5:\"daily\";s:4:\"args\";a:0:{}s:8:\"interval\";i:86400;}}}i:1454151960;a:1:{s:20:\"wp_maybe_auto_update\";a:1:{s:32:\"40cd750bba9870f18aada2478b24840a\";a:3:{s:8:\"schedule\";s:10:\"twicedaily\";s:4:\"args\";a:0:{}s:8:\"interval\";i:43200;}}}i:1454161328;a:3:{s:16:\"wp_version_check\";a:1:{s:32:\"40cd750bba9870f18aada2478b24840a\";a:3:{s:8:\"schedule\";s:10:\"twicedaily\";s:4:\"args\";a:0:{}s:8:\"interval\";i:43200;}}s:17:\"wp_update_plugins\";a:1:{s:32:\"40cd750bba9870f18aada2478b24840a\";a:3:{s:8:\"schedule\";s:10:\"twicedaily\";s:4:\"args\";a:0:{}s:8:\"interval\";i:43200;}}s:16:\"wp_update_themes\";a:1:{s:32:\"40cd750bba9870f18aada2478b24840a\";a:3:{s:8:\"schedule\";s:10:\"twicedaily\";s:4:\"args\";a:0:{}s:8:\"interval\";i:43200;}}}s:7:\"version\";i:2;}', 'yes'), ('102', 'rewrite_rules', 'a:58:{s:48:\".*wp-(atom|rdf|rss|rss2|feed|commentsrss2)\\.php$\";s:18:\"index.php?feed=old\";s:20:\".*wp-app\\.php(/.*)?$\";s:19:\"index.php?error=403\";s:18:\".*wp-register.php$\";s:23:\"index.php?register=true\";s:42:\"index.php/feed/(feed|rdf|rss|rss2|atom)/?$\";s:27:\"index.php?&feed=$matches[1]\";s:37:\"index.php/(feed|rdf|rss|rss2|atom)/?$\";s:27:\"index.php?&feed=$matches[1]\";s:30:\"index.php/page/?([0-9]{1,})/?$\";s:28:\"index.php?&paged=$matches[1]\";s:51:\"index.php/comments/feed/(feed|rdf|rss|rss2|atom)/?$\";s:42:\"index.php?&feed=$matches[1]&withcomments=1\";s:46:\"index.php/comments/(feed|rdf|rss|rss2|atom)/?$\";s:42:\"index.php?&feed=$matches[1]&withcomments=1\";s:54:\"index.php/search/(.+)/feed/(feed|rdf|rss|rss2|atom)/?$\";s:40:\"index.php?s=$matches[1]&feed=$matches[2]\";s:49:\"index.php/search/(.+)/(feed|rdf|rss|rss2|atom)/?$\";s:40:\"index.php?s=$matches[1]&feed=$matches[2]\";s:42:\"index.php/search/(.+)/page/?([0-9]{1,})/?$\";s:41:\"index.php?s=$matches[1]&paged=$matches[2]\";s:24:\"index.php/search/(.+)/?$\";s:23:\"index.php?s=$matches[1]\";s:57:\"index.php/author/([^/]+)/feed/(feed|rdf|rss|rss2|atom)/?$\";s:50:\"index.php?author_name=$matches[1]&feed=$matches[2]\";s:52:\"index.php/author/([^/]+)/(feed|rdf|rss|rss2|atom)/?$\";s:50:\"index.php?author_name=$matches[1]&feed=$matches[2]\";s:45:\"index.php/author/([^/]+)/page/?([0-9]{1,})/?$\";s:51:\"index.php?author_name=$matches[1]&paged=$matches[2]\";s:27:\"index.php/author/([^/]+)/?$\";s:33:\"index.php?author_name=$matches[1]\";s:79:\"index.php/([0-9]{4})/([0-9]{1,2})/([0-9]{1,2})/feed/(feed|rdf|rss|rss2|atom)/?$\";s:80:\"index.php?year=$matches[1]&monthnum=$matches[2]&day=$matches[3]&feed=$matches[4]\";s:74:\"index.php/([0-9]{4})/([0-9]{1,2})/([0-9]{1,2})/(feed|rdf|rss|rss2|atom)/?$\";s:80:\"index.php?year=$matches[1]&monthnum=$matches[2]&day=$matches[3]&feed=$matches[4]\";s:67:\"index.php/([0-9]{4})/([0-9]{1,2})/([0-9]{1,2})/page/?([0-9]{1,})/?$\";s:81:\"index.php?year=$matches[1]&monthnum=$matches[2]&day=$matches[3]&paged=$matches[4]\";s:49:\"index.php/([0-9]{4})/([0-9]{1,2})/([0-9]{1,2})/?$\";s:63:\"index.php?year=$matches[1]&monthnum=$matches[2]&day=$matches[3]\";s:66:\"index.php/([0-9]{4})/([0-9]{1,2})/feed/(feed|rdf|rss|rss2|atom)/?$\";s:64:\"index.php?year=$matches[1]&monthnum=$matches[2]&feed=$matches[3]\";s:61:\"index.php/([0-9]{4})/([0-9]{1,2})/(feed|rdf|rss|rss2|atom)/?$\";s:64:\"index.php?year=$matches[1]&monthnum=$matches[2]&feed=$matches[3]\";s:54:\"index.php/([0-9]{4})/([0-9]{1,2})/page/?([0-9]{1,})/?$\";s:65:\"index.php?year=$matches[1]&monthnum=$matches[2]&paged=$matches[3]\";s:36:\"index.php/([0-9]{4})/([0-9]{1,2})/?$\";s:47:\"index.php?year=$matches[1]&monthnum=$matches[2]\";s:53:\"index.php/([0-9]{4})/feed/(feed|rdf|rss|rss2|atom)/?$\";s:43:\"index.php?year=$matches[1]&feed=$matches[2]\";s:48:\"index.php/([0-9]{4})/(feed|rdf|rss|rss2|atom)/?$\";s:43:\"index.php?year=$matches[1]&feed=$matches[2]\";s:41:\"index.php/([0-9]{4})/page/?([0-9]{1,})/?$\";s:44:\"index.php?year=$matches[1]&paged=$matches[2]\";s:23:\"index.php/([0-9]{4})/?$\";s:26:\"index.php?year=$matches[1]\";s:68:\"index.php/[0-9]{4}/[0-9]{1,2}/[0-9]{1,2}/[^/]+/attachment/([^/]+)/?$\";s:32:\"index.php?attachment=$matches[1]\";s:78:\"index.php/[0-9]{4}/[0-9]{1,2}/[0-9]{1,2}/[^/]+/attachment/([^/]+)/trackback/?$\";s:37:\"index.php?attachment=$matches[1]&tb=1\";s:98:\"index.php/[0-9]{4}/[0-9]{1,2}/[0-9]{1,2}/[^/]+/attachment/([^/]+)/feed/(feed|rdf|rss|rss2|atom)/?$\";s:49:\"index.php?attachment=$matches[1]&feed=$matches[2]\";s:93:\"index.php/[0-9]{4}/[0-9]{1,2}/[0-9]{1,2}/[^/]+/attachment/([^/]+)/(feed|rdf|rss|rss2|atom)/?$\";s:49:\"index.php?attachment=$matches[1]&feed=$matches[2]\";s:93:\"index.php/[0-9]{4}/[0-9]{1,2}/[0-9]{1,2}/[^/]+/attachment/([^/]+)/comment-page-([0-9]{1,})/?$\";s:50:\"index.php?attachment=$matches[1]&cpage=$matches[2]\";s:67:\"index.php/([0-9]{4})/([0-9]{1,2})/([0-9]{1,2})/([^/]+)/trackback/?$\";s:85:\"index.php?year=$matches[1]&monthnum=$matches[2]&day=$matches[3]&name=$matches[4]&tb=1\";s:87:\"index.php/([0-9]{4})/([0-9]{1,2})/([0-9]{1,2})/([^/]+)/feed/(feed|rdf|rss|rss2|atom)/?$\";s:97:\"index.php?year=$matches[1]&monthnum=$matches[2]&day=$matches[3]&name=$matches[4]&feed=$matches[5]\";s:82:\"index.php/([0-9]{4})/([0-9]{1,2})/([0-9]{1,2})/([^/]+)/(feed|rdf|rss|rss2|atom)/?$\";s:97:\"index.php?year=$matches[1]&monthnum=$matches[2]&day=$matches[3]&name=$matches[4]&feed=$matches[5]\";s:75:\"index.php/([0-9]{4})/([0-9]{1,2})/([0-9]{1,2})/([^/]+)/page/?([0-9]{1,})/?$\";s:98:\"index.php?year=$matches[1]&monthnum=$matches[2]&day=$matches[3]&name=$matches[4]&paged=$matches[5]\";s:82:\"index.php/([0-9]{4})/([0-9]{1,2})/([0-9]{1,2})/([^/]+)/comment-page-([0-9]{1,})/?$\";s:98:\"index.php?year=$matches[1]&monthnum=$matches[2]&day=$matches[3]&name=$matches[4]&cpage=$matches[5]\";s:67:\"index.php/([0-9]{4})/([0-9]{1,2})/([0-9]{1,2})/([^/]+)(/[0-9]+)?/?$\";s:97:\"index.php?year=$matches[1]&monthnum=$matches[2]&day=$matches[3]&name=$matches[4]&page=$matches[5]\";s:57:\"index.php/[0-9]{4}/[0-9]{1,2}/[0-9]{1,2}/[^/]+/([^/]+)/?$\";s:32:\"index.php?attachment=$matches[1]\";s:67:\"index.php/[0-9]{4}/[0-9]{1,2}/[0-9]{1,2}/[^/]+/([^/]+)/trackback/?$\";s:37:\"index.php?attachment=$matches[1]&tb=1\";s:87:\"index.php/[0-9]{4}/[0-9]{1,2}/[0-9]{1,2}/[^/]+/([^/]+)/feed/(feed|rdf|rss|rss2|atom)/?$\";s:49:\"index.php?attachment=$matches[1]&feed=$matches[2]\";s:82:\"index.php/[0-9]{4}/[0-9]{1,2}/[0-9]{1,2}/[^/]+/([^/]+)/(feed|rdf|rss|rss2|atom)/?$\";s:49:\"index.php?attachment=$matches[1]&feed=$matches[2]\";s:82:\"index.php/[0-9]{4}/[0-9]{1,2}/[0-9]{1,2}/[^/]+/([^/]+)/comment-page-([0-9]{1,})/?$\";s:50:\"index.php?attachment=$matches[1]&cpage=$matches[2]\";s:74:\"index.php/([0-9]{4})/([0-9]{1,2})/([0-9]{1,2})/comment-page-([0-9]{1,})/?$\";s:81:\"index.php?year=$matches[1]&monthnum=$matches[2]&day=$matches[3]&cpage=$matches[4]\";s:61:\"index.php/([0-9]{4})/([0-9]{1,2})/comment-page-([0-9]{1,})/?$\";s:65:\"index.php?year=$matches[1]&monthnum=$matches[2]&cpage=$matches[3]\";s:48:\"index.php/([0-9]{4})/comment-page-([0-9]{1,})/?$\";s:44:\"index.php?year=$matches[1]&cpage=$matches[2]\";s:37:\"index.php/.?.+?/attachment/([^/]+)/?$\";s:32:\"index.php?attachment=$matches[1]\";s:47:\"index.php/.?.+?/attachment/([^/]+)/trackback/?$\";s:37:\"index.php?attachment=$matches[1]&tb=1\";s:67:\"index.php/.?.+?/attachment/([^/]+)/feed/(feed|rdf|rss|rss2|atom)/?$\";s:49:\"index.php?attachment=$matches[1]&feed=$matches[2]\";s:62:\"index.php/.?.+?/attachment/([^/]+)/(feed|rdf|rss|rss2|atom)/?$\";s:49:\"index.php?attachment=$matches[1]&feed=$matches[2]\";s:62:\"index.php/.?.+?/attachment/([^/]+)/comment-page-([0-9]{1,})/?$\";s:50:\"index.php?attachment=$matches[1]&cpage=$matches[2]\";s:30:\"index.php/(.?.+?)/trackback/?$\";s:35:\"index.php?pagename=$matches[1]&tb=1\";s:50:\"index.php/(.?.+?)/feed/(feed|rdf|rss|rss2|atom)/?$\";s:47:\"index.php?pagename=$matches[1]&feed=$matches[2]\";s:45:\"index.php/(.?.+?)/(feed|rdf|rss|rss2|atom)/?$\";s:47:\"index.php?pagename=$matches[1]&feed=$matches[2]\";s:38:\"index.php/(.?.+?)/page/?([0-9]{1,})/?$\";s:48:\"index.php?pagename=$matches[1]&paged=$matches[2]\";s:45:\"index.php/(.?.+?)/comment-page-([0-9]{1,})/?$\";s:48:\"index.php?pagename=$matches[1]&cpage=$matches[2]\";s:30:\"index.php/(.?.+?)(/[0-9]+)?/?$\";s:47:\"index.php?pagename=$matches[1]&page=$matches[2]\";}', 'yes'), ('110', '_transient_random_seed', 'fc28bd90d5866043f50399d447315316', 'yes'), ('112', '_site_transient_timeout_browser_4743e16edc1bd1d0246226b06db587c3', '1449754947', 'yes'), ('113', '_site_transient_browser_4743e16edc1bd1d0246226b06db587c3', 'a:9:{s:8:\"platform\";s:9:\"Macintosh\";s:4:\"name\";s:6:\"Chrome\";s:7:\"version\";s:12:\"39.0.2171.95\";s:10:\"update_url\";s:28:\"http://www.google.com/chrome\";s:7:\"img_src\";s:49:\"http://s.wordpress.org/images/browsers/chrome.png\";s:11:\"img_src_ssl\";s:48:\"https://wordpress.org/images/browsers/chrome.png\";s:15:\"current_version\";s:2:\"18\";s:7:\"upgrade\";b:0;s:8:\"insecure\";b:0;}', 'yes'), ('114', 'can_compress_scripts', '1', 'yes'), ('148', 'recently_activated', 'a:0:{}', 'yes'), ('155', 'category_children', 'a:0:{}', 'yes'), ('166', '_transient_timeout_plugin_slugs', '1449586023', 'no'), ('167', '_transient_plugin_slugs', 'a:2:{i:0;s:19:\"akismet/akismet.php\";i:1;s:9:\"hello.php\";}', 'no'), ('168', '_transient_timeout_dash_5438fb5baf31c513fff2b9a1067656a6', '1449541845', 'no'), ('169', '_transient_dash_5438fb5baf31c513fff2b9a1067656a6', '<div class=\"rss-widget\"><p><strong>RSS错误</strong>：WP HTTP Error: Could not resolve host: cn.wordpress.org</p></div><div class=\"rss-widget\"><p><strong>RSS错误</strong>：WP HTTP Error: Resolving timed out after 10520 milliseconds</p></div><div class=\"rss-widget\"><ul></ul></div>', 'no'), ('171', '_site_transient_timeout_poptags_40cd750bba9870f18aada2478b24840a', '1449509905', 'yes'), ('172', '_site_transient_poptags_40cd750bba9870f18aada2478b24840a', 'a:100:{s:6:\"widget\";a:3:{s:4:\"name\";s:6:\"widget\";s:4:\"slug\";s:6:\"widget\";s:5:\"count\";s:4:\"5590\";}s:4:\"post\";a:3:{s:4:\"name\";s:4:\"Post\";s:4:\"slug\";s:4:\"post\";s:5:\"count\";s:4:\"3496\";}s:6:\"plugin\";a:3:{s:4:\"name\";s:6:\"plugin\";s:4:\"slug\";s:6:\"plugin\";s:5:\"count\";s:4:\"3442\";}s:5:\"admin\";a:3:{s:4:\"name\";s:5:\"admin\";s:4:\"slug\";s:5:\"admin\";s:5:\"count\";s:4:\"2953\";}s:5:\"posts\";a:3:{s:4:\"name\";s:5:\"posts\";s:4:\"slug\";s:5:\"posts\";s:5:\"count\";s:4:\"2691\";}s:9:\"shortcode\";a:3:{s:4:\"name\";s:9:\"shortcode\";s:4:\"slug\";s:9:\"shortcode\";s:5:\"count\";s:4:\"2153\";}s:7:\"sidebar\";a:3:{s:4:\"name\";s:7:\"sidebar\";s:4:\"slug\";s:7:\"sidebar\";s:5:\"count\";s:4:\"2143\";}s:6:\"google\";a:3:{s:4:\"name\";s:6:\"google\";s:4:\"slug\";s:6:\"google\";s:5:\"count\";s:4:\"1967\";}s:7:\"twitter\";a:3:{s:4:\"name\";s:7:\"twitter\";s:4:\"slug\";s:7:\"twitter\";s:5:\"count\";s:4:\"1927\";}s:6:\"images\";a:3:{s:4:\"name\";s:6:\"images\";s:4:\"slug\";s:6:\"images\";s:5:\"count\";s:4:\"1908\";}s:4:\"page\";a:3:{s:4:\"name\";s:4:\"page\";s:4:\"slug\";s:4:\"page\";s:5:\"count\";s:4:\"1902\";}s:8:\"comments\";a:3:{s:4:\"name\";s:8:\"comments\";s:4:\"slug\";s:8:\"comments\";s:5:\"count\";s:4:\"1859\";}s:5:\"image\";a:3:{s:4:\"name\";s:5:\"image\";s:4:\"slug\";s:5:\"image\";s:5:\"count\";s:4:\"1755\";}s:8:\"facebook\";a:3:{s:4:\"name\";s:8:\"Facebook\";s:4:\"slug\";s:8:\"facebook\";s:5:\"count\";s:4:\"1564\";}s:3:\"seo\";a:3:{s:4:\"name\";s:3:\"seo\";s:4:\"slug\";s:3:\"seo\";s:5:\"count\";s:4:\"1481\";}s:9:\"wordpress\";a:3:{s:4:\"name\";s:9:\"wordpress\";s:4:\"slug\";s:9:\"wordpress\";s:5:\"count\";s:4:\"1454\";}s:11:\"woocommerce\";a:3:{s:4:\"name\";s:11:\"woocommerce\";s:4:\"slug\";s:11:\"woocommerce\";s:5:\"count\";s:4:\"1339\";}s:6:\"social\";a:3:{s:4:\"name\";s:6:\"social\";s:4:\"slug\";s:6:\"social\";s:5:\"count\";s:4:\"1272\";}s:5:\"links\";a:3:{s:4:\"name\";s:5:\"links\";s:4:\"slug\";s:5:\"links\";s:5:\"count\";s:4:\"1243\";}s:7:\"gallery\";a:3:{s:4:\"name\";s:7:\"gallery\";s:4:\"slug\";s:7:\"gallery\";s:5:\"count\";s:4:\"1221\";}s:5:\"email\";a:3:{s:4:\"name\";s:5:\"email\";s:4:\"slug\";s:5:\"email\";s:5:\"count\";s:4:\"1117\";}s:7:\"widgets\";a:3:{s:4:\"name\";s:7:\"widgets\";s:4:\"slug\";s:7:\"widgets\";s:5:\"count\";s:4:\"1048\";}s:5:\"pages\";a:3:{s:4:\"name\";s:5:\"pages\";s:4:\"slug\";s:5:\"pages\";s:5:\"count\";s:4:\"1011\";}s:6:\"jquery\";a:3:{s:4:\"name\";s:6:\"jquery\";s:4:\"slug\";s:6:\"jquery\";s:5:\"count\";s:3:\"968\";}s:5:\"media\";a:3:{s:4:\"name\";s:5:\"media\";s:4:\"slug\";s:5:\"media\";s:5:\"count\";s:3:\"928\";}s:3:\"rss\";a:3:{s:4:\"name\";s:3:\"rss\";s:4:\"slug\";s:3:\"rss\";s:5:\"count\";s:3:\"898\";}s:4:\"ajax\";a:3:{s:4:\"name\";s:4:\"AJAX\";s:4:\"slug\";s:4:\"ajax\";s:5:\"count\";s:3:\"864\";}s:5:\"video\";a:3:{s:4:\"name\";s:5:\"video\";s:4:\"slug\";s:5:\"video\";s:5:\"count\";s:3:\"856\";}s:9:\"ecommerce\";a:3:{s:4:\"name\";s:9:\"ecommerce\";s:4:\"slug\";s:9:\"ecommerce\";s:5:\"count\";s:3:\"856\";}s:7:\"content\";a:3:{s:4:\"name\";s:7:\"content\";s:4:\"slug\";s:7:\"content\";s:5:\"count\";s:3:\"855\";}s:5:\"login\";a:3:{s:4:\"name\";s:5:\"login\";s:4:\"slug\";s:5:\"login\";s:5:\"count\";s:3:\"831\";}s:10:\"javascript\";a:3:{s:4:\"name\";s:10:\"javascript\";s:4:\"slug\";s:10:\"javascript\";s:5:\"count\";s:3:\"792\";}s:10:\"buddypress\";a:3:{s:4:\"name\";s:10:\"buddypress\";s:4:\"slug\";s:10:\"buddypress\";s:5:\"count\";s:3:\"754\";}s:5:\"photo\";a:3:{s:4:\"name\";s:5:\"photo\";s:4:\"slug\";s:5:\"photo\";s:5:\"count\";s:3:\"723\";}s:4:\"feed\";a:3:{s:4:\"name\";s:4:\"feed\";s:4:\"slug\";s:4:\"feed\";s:5:\"count\";s:3:\"717\";}s:7:\"youtube\";a:3:{s:4:\"name\";s:7:\"youtube\";s:4:\"slug\";s:7:\"youtube\";s:5:\"count\";s:3:\"717\";}s:8:\"security\";a:3:{s:4:\"name\";s:8:\"security\";s:4:\"slug\";s:8:\"security\";s:5:\"count\";s:3:\"716\";}s:10:\"responsive\";a:3:{s:4:\"name\";s:10:\"responsive\";s:4:\"slug\";s:10:\"responsive\";s:5:\"count\";s:3:\"711\";}s:4:\"link\";a:3:{s:4:\"name\";s:4:\"link\";s:4:\"slug\";s:4:\"link\";s:5:\"count\";s:3:\"705\";}s:4:\"spam\";a:3:{s:4:\"name\";s:4:\"spam\";s:4:\"slug\";s:4:\"spam\";s:5:\"count\";s:3:\"696\";}s:5:\"share\";a:3:{s:4:\"name\";s:5:\"Share\";s:4:\"slug\";s:5:\"share\";s:5:\"count\";s:3:\"694\";}s:10:\"e-commerce\";a:3:{s:4:\"name\";s:10:\"e-commerce\";s:4:\"slug\";s:10:\"e-commerce\";s:5:\"count\";s:3:\"678\";}s:6:\"photos\";a:3:{s:4:\"name\";s:6:\"photos\";s:4:\"slug\";s:6:\"photos\";s:5:\"count\";s:3:\"671\";}s:8:\"category\";a:3:{s:4:\"name\";s:8:\"category\";s:4:\"slug\";s:8:\"category\";s:5:\"count\";s:3:\"664\";}s:5:\"embed\";a:3:{s:4:\"name\";s:5:\"embed\";s:4:\"slug\";s:5:\"embed\";s:5:\"count\";s:3:\"638\";}s:9:\"analytics\";a:3:{s:4:\"name\";s:9:\"analytics\";s:4:\"slug\";s:9:\"analytics\";s:5:\"count\";s:3:\"638\";}s:4:\"form\";a:3:{s:4:\"name\";s:4:\"form\";s:4:\"slug\";s:4:\"form\";s:5:\"count\";s:3:\"628\";}s:3:\"css\";a:3:{s:4:\"name\";s:3:\"CSS\";s:4:\"slug\";s:3:\"css\";s:5:\"count\";s:3:\"624\";}s:6:\"search\";a:3:{s:4:\"name\";s:6:\"search\";s:4:\"slug\";s:6:\"search\";s:5:\"count\";s:3:\"621\";}s:9:\"slideshow\";a:3:{s:4:\"name\";s:9:\"slideshow\";s:4:\"slug\";s:9:\"slideshow\";s:5:\"count\";s:3:\"618\";}s:6:\"custom\";a:3:{s:4:\"name\";s:6:\"custom\";s:4:\"slug\";s:6:\"custom\";s:5:\"count\";s:3:\"593\";}s:5:\"stats\";a:3:{s:4:\"name\";s:5:\"stats\";s:4:\"slug\";s:5:\"stats\";s:5:\"count\";s:3:\"588\";}s:6:\"slider\";a:3:{s:4:\"name\";s:6:\"slider\";s:4:\"slug\";s:6:\"slider\";s:5:\"count\";s:3:\"580\";}s:7:\"comment\";a:3:{s:4:\"name\";s:7:\"comment\";s:4:\"slug\";s:7:\"comment\";s:5:\"count\";s:3:\"575\";}s:6:\"button\";a:3:{s:4:\"name\";s:6:\"button\";s:4:\"slug\";s:6:\"button\";s:5:\"count\";s:3:\"569\";}s:4:\"menu\";a:3:{s:4:\"name\";s:4:\"menu\";s:4:\"slug\";s:4:\"menu\";s:5:\"count\";s:3:\"566\";}s:5:\"theme\";a:3:{s:4:\"name\";s:5:\"theme\";s:4:\"slug\";s:5:\"theme\";s:5:\"count\";s:3:\"564\";}s:4:\"tags\";a:3:{s:4:\"name\";s:4:\"tags\";s:4:\"slug\";s:4:\"tags\";s:5:\"count\";s:3:\"562\";}s:9:\"dashboard\";a:3:{s:4:\"name\";s:9:\"dashboard\";s:4:\"slug\";s:9:\"dashboard\";s:5:\"count\";s:3:\"558\";}s:10:\"categories\";a:3:{s:4:\"name\";s:10:\"categories\";s:4:\"slug\";s:10:\"categories\";s:5:\"count\";s:3:\"551\";}s:10:\"statistics\";a:3:{s:4:\"name\";s:10:\"statistics\";s:4:\"slug\";s:10:\"statistics\";s:5:\"count\";s:3:\"537\";}s:3:\"ads\";a:3:{s:4:\"name\";s:3:\"ads\";s:4:\"slug\";s:3:\"ads\";s:5:\"count\";s:3:\"524\";}s:6:\"mobile\";a:3:{s:4:\"name\";s:6:\"mobile\";s:4:\"slug\";s:6:\"mobile\";s:5:\"count\";s:3:\"520\";}s:4:\"user\";a:3:{s:4:\"name\";s:4:\"user\";s:4:\"slug\";s:4:\"user\";s:5:\"count\";s:3:\"512\";}s:6:\"editor\";a:3:{s:4:\"name\";s:6:\"editor\";s:4:\"slug\";s:6:\"editor\";s:5:\"count\";s:3:\"509\";}s:5:\"users\";a:3:{s:4:\"name\";s:5:\"users\";s:4:\"slug\";s:5:\"users\";s:5:\"count\";s:3:\"498\";}s:7:\"picture\";a:3:{s:4:\"name\";s:7:\"picture\";s:4:\"slug\";s:7:\"picture\";s:5:\"count\";s:3:\"497\";}s:4:\"list\";a:3:{s:4:\"name\";s:4:\"list\";s:4:\"slug\";s:4:\"list\";s:5:\"count\";s:3:\"494\";}s:7:\"plugins\";a:3:{s:4:\"name\";s:7:\"plugins\";s:4:\"slug\";s:7:\"plugins\";s:5:\"count\";s:3:\"493\";}s:9:\"affiliate\";a:3:{s:4:\"name\";s:9:\"affiliate\";s:4:\"slug\";s:9:\"affiliate\";s:5:\"count\";s:3:\"489\";}s:9:\"multisite\";a:3:{s:4:\"name\";s:9:\"multisite\";s:4:\"slug\";s:9:\"multisite\";s:5:\"count\";s:3:\"464\";}s:6:\"simple\";a:3:{s:4:\"name\";s:6:\"simple\";s:4:\"slug\";s:6:\"simple\";s:5:\"count\";s:3:\"461\";}s:12:\"contact-form\";a:3:{s:4:\"name\";s:12:\"contact form\";s:4:\"slug\";s:12:\"contact-form\";s:5:\"count\";s:3:\"453\";}s:8:\"pictures\";a:3:{s:4:\"name\";s:8:\"pictures\";s:4:\"slug\";s:8:\"pictures\";s:5:\"count\";s:3:\"448\";}s:7:\"contact\";a:3:{s:4:\"name\";s:7:\"contact\";s:4:\"slug\";s:7:\"contact\";s:5:\"count\";s:3:\"442\";}s:12:\"social-media\";a:3:{s:4:\"name\";s:12:\"social media\";s:4:\"slug\";s:12:\"social-media\";s:5:\"count\";s:3:\"442\";}s:10:\"navigation\";a:3:{s:4:\"name\";s:10:\"navigation\";s:4:\"slug\";s:10:\"navigation\";s:5:\"count\";s:3:\"425\";}s:5:\"flash\";a:3:{s:4:\"name\";s:5:\"flash\";s:4:\"slug\";s:5:\"flash\";s:5:\"count\";s:3:\"420\";}s:3:\"url\";a:3:{s:4:\"name\";s:3:\"url\";s:4:\"slug\";s:3:\"url\";s:5:\"count\";s:3:\"414\";}s:4:\"html\";a:3:{s:4:\"name\";s:4:\"html\";s:4:\"slug\";s:4:\"html\";s:5:\"count\";s:3:\"413\";}s:10:\"newsletter\";a:3:{s:4:\"name\";s:10:\"newsletter\";s:4:\"slug\";s:10:\"newsletter\";s:5:\"count\";s:3:\"406\";}s:3:\"api\";a:3:{s:4:\"name\";s:3:\"api\";s:4:\"slug\";s:3:\"api\";s:5:\"count\";s:3:\"406\";}s:4:\"shop\";a:3:{s:4:\"name\";s:4:\"shop\";s:4:\"slug\";s:4:\"shop\";s:5:\"count\";s:3:\"400\";}s:4:\"meta\";a:3:{s:4:\"name\";s:4:\"meta\";s:4:\"slug\";s:4:\"meta\";s:5:\"count\";s:3:\"396\";}s:4:\"news\";a:3:{s:4:\"name\";s:4:\"News\";s:4:\"slug\";s:4:\"news\";s:5:\"count\";s:3:\"393\";}s:9:\"marketing\";a:3:{s:4:\"name\";s:9:\"marketing\";s:4:\"slug\";s:9:\"marketing\";s:5:\"count\";s:3:\"392\";}s:3:\"tag\";a:3:{s:4:\"name\";s:3:\"tag\";s:4:\"slug\";s:3:\"tag\";s:5:\"count\";s:3:\"390\";}s:6:\"events\";a:3:{s:4:\"name\";s:6:\"events\";s:4:\"slug\";s:6:\"events\";s:5:\"count\";s:3:\"385\";}s:8:\"tracking\";a:3:{s:4:\"name\";s:8:\"tracking\";s:4:\"slug\";s:8:\"tracking\";s:5:\"count\";s:3:\"382\";}s:8:\"calendar\";a:3:{s:4:\"name\";s:8:\"calendar\";s:4:\"slug\";s:8:\"calendar\";s:5:\"count\";s:3:\"380\";}s:9:\"thumbnail\";a:3:{s:4:\"name\";s:9:\"thumbnail\";s:4:\"slug\";s:9:\"thumbnail\";s:5:\"count\";s:3:\"379\";}s:11:\"advertising\";a:3:{s:4:\"name\";s:11:\"advertising\";s:4:\"slug\";s:11:\"advertising\";s:5:\"count\";s:3:\"377\";}s:4:\"text\";a:3:{s:4:\"name\";s:4:\"text\";s:4:\"slug\";s:4:\"text\";s:5:\"count\";s:3:\"376\";}s:4:\"code\";a:3:{s:4:\"name\";s:4:\"code\";s:4:\"slug\";s:4:\"code\";s:5:\"count\";s:3:\"374\";}s:8:\"lightbox\";a:3:{s:4:\"name\";s:8:\"lightbox\";s:4:\"slug\";s:8:\"lightbox\";s:5:\"count\";s:3:\"368\";}s:6:\"upload\";a:3:{s:4:\"name\";s:6:\"upload\";s:4:\"slug\";s:6:\"upload\";s:5:\"count\";s:3:\"368\";}s:10:\"shortcodes\";a:3:{s:4:\"name\";s:10:\"shortcodes\";s:4:\"slug\";s:10:\"shortcodes\";s:5:\"count\";s:3:\"365\";}s:9:\"automatic\";a:3:{s:4:\"name\";s:9:\"automatic\";s:4:\"slug\";s:9:\"automatic\";s:5:\"count\";s:3:\"363\";}s:7:\"profile\";a:3:{s:4:\"name\";s:7:\"profile\";s:4:\"slug\";s:7:\"profile\";s:5:\"count\";s:3:\"361\";}s:7:\"sharing\";a:3:{s:4:\"name\";s:7:\"sharing\";s:4:\"slug\";s:7:\"sharing\";s:5:\"count\";s:3:\"360\";}}', 'yes'), ('173', 'ftp_credentials', 'a:3:{s:8:\"hostname\";s:9:\"127.0.0.1\";s:8:\"username\";s:5:\"admin\";s:15:\"connection_type\";s:4:\"ftps\";}', 'yes'), ('176', '_transient_is_multi_author', '0', 'yes'), ('177', '_transient_twentyfifteen_categories', '1', 'yes'), ('178', '_site_transient_timeout_theme_roots', '1454123188', 'yes'), ('179', '_site_transient_theme_roots', 'a:3:{s:13:\"twentyfifteen\";s:7:\"/themes\";s:14:\"twentyfourteen\";s:7:\"/themes\";s:14:\"twentythirteen\";s:7:\"/themes\";}', 'yes'), ('183', '_site_transient_update_core', 'O:8:\"stdClass\":4:{s:7:\"updates\";a:3:{i:0;O:8:\"stdClass\":10:{s:8:\"response\";s:7:\"upgrade\";s:8:\"download\";s:65:\"https://downloads.wordpress.org/release/zh_CN/wordpress-4.4.1.zip\";s:6:\"locale\";s:5:\"zh_CN\";s:8:\"packages\";O:8:\"stdClass\":5:{s:4:\"full\";s:65:\"https://downloads.wordpress.org/release/zh_CN/wordpress-4.4.1.zip\";s:10:\"no_content\";b:0;s:11:\"new_bundled\";b:0;s:7:\"partial\";b:0;s:8:\"rollback\";b:0;}s:7:\"current\";s:5:\"4.4.1\";s:7:\"version\";s:5:\"4.4.1\";s:11:\"php_version\";s:5:\"5.2.4\";s:13:\"mysql_version\";s:3:\"5.0\";s:11:\"new_bundled\";s:3:\"4.4\";s:15:\"partial_version\";s:0:\"\";}i:1;O:8:\"stdClass\":10:{s:8:\"response\";s:7:\"upgrade\";s:8:\"download\";s:59:\"https://downloads.wordpress.org/release/wordpress-4.4.1.zip\";s:6:\"locale\";s:5:\"en_US\";s:8:\"packages\";O:8:\"stdClass\":5:{s:4:\"full\";s:59:\"https://downloads.wordpress.org/release/wordpress-4.4.1.zip\";s:10:\"no_content\";s:70:\"https://downloads.wordpress.org/release/wordpress-4.4.1-no-content.zip\";s:11:\"new_bundled\";s:71:\"https://downloads.wordpress.org/release/wordpress-4.4.1-new-bundled.zip\";s:7:\"partial\";b:0;s:8:\"rollback\";b:0;}s:7:\"current\";s:5:\"4.4.1\";s:7:\"version\";s:5:\"4.4.1\";s:11:\"php_version\";s:5:\"5.2.4\";s:13:\"mysql_version\";s:3:\"5.0\";s:11:\"new_bundled\";s:3:\"4.4\";s:15:\"partial_version\";s:0:\"\";}i:2;O:8:\"stdClass\":11:{s:8:\"response\";s:10:\"autoupdate\";s:8:\"download\";s:65:\"https://downloads.wordpress.org/release/zh_CN/wordpress-4.4.1.zip\";s:6:\"locale\";s:5:\"zh_CN\";s:8:\"packages\";O:8:\"stdClass\":5:{s:4:\"full\";s:65:\"https://downloads.wordpress.org/release/zh_CN/wordpress-4.4.1.zip\";s:10:\"no_content\";b:0;s:11:\"new_bundled\";b:0;s:7:\"partial\";b:0;s:8:\"rollback\";b:0;}s:7:\"current\";s:5:\"4.4.1\";s:7:\"version\";s:5:\"4.4.1\";s:11:\"php_version\";s:5:\"5.2.4\";s:13:\"mysql_version\";s:3:\"5.0\";s:11:\"new_bundled\";s:3:\"4.4\";s:15:\"partial_version\";s:0:\"\";s:9:\"new_files\";s:1:\"1\";}}s:12:\"last_checked\";i:1454121414;s:15:\"version_checked\";s:5:\"4.3.2\";s:12:\"translations\";a:1:{i:0;a:7:{s:4:\"type\";s:4:\"core\";s:4:\"slug\";s:7:\"default\";s:8:\"language\";s:5:\"zh_CN\";s:7:\"version\";s:5:\"4.3.2\";s:7:\"updated\";s:19:\"2015-08-20 19:10:20\";s:7:\"package\";s:64:\"https://downloads.wordpress.org/translation/core/4.3.2/zh_CN.zip\";s:10:\"autoupdate\";b:1;}}}', 'yes'), ('184', '_site_transient_update_themes', 'O:8:\"stdClass\":4:{s:12:\"last_checked\";i:1454121417;s:7:\"checked\";a:3:{s:13:\"twentyfifteen\";s:3:\"1.3\";s:14:\"twentyfourteen\";s:3:\"1.5\";s:14:\"twentythirteen\";s:3:\"1.6\";}s:8:\"response\";a:3:{s:13:\"twentyfifteen\";a:4:{s:5:\"theme\";s:13:\"twentyfifteen\";s:11:\"new_version\";s:3:\"1.4\";s:3:\"url\";s:43:\"https://wordpress.org/themes/twentyfifteen/\";s:7:\"package\";s:59:\"https://downloads.wordpress.org/theme/twentyfifteen.1.4.zip\";}s:14:\"twentyfourteen\";a:4:{s:5:\"theme\";s:14:\"twentyfourteen\";s:11:\"new_version\";s:3:\"1.6\";s:3:\"url\";s:44:\"https://wordpress.org/themes/twentyfourteen/\";s:7:\"package\";s:60:\"https://downloads.wordpress.org/theme/twentyfourteen.1.6.zip\";}s:14:\"twentythirteen\";a:4:{s:5:\"theme\";s:14:\"twentythirteen\";s:11:\"new_version\";s:3:\"1.7\";s:3:\"url\";s:44:\"https://wordpress.org/themes/twentythirteen/\";s:7:\"package\";s:60:\"https://downloads.wordpress.org/theme/twentythirteen.1.7.zip\";}}s:12:\"translations\";a:1:{i:0;a:7:{s:4:\"type\";s:5:\"theme\";s:4:\"slug\";s:13:\"twentyfifteen\";s:8:\"language\";s:5:\"zh_CN\";s:7:\"version\";s:3:\"1.3\";s:7:\"updated\";s:19:\"2015-08-20 19:10:21\";s:7:\"package\";s:77:\"https://downloads.wordpress.org/translation/theme/twentyfifteen/1.3/zh_CN.zip\";s:10:\"autoupdate\";b:1;}}}', 'yes'), ('185', '_site_transient_update_plugins', 'O:8:\"stdClass\":4:{s:12:\"last_checked\";i:1454121415;s:8:\"response\";a:1:{s:19:\"akismet/akismet.php\";O:8:\"stdClass\":6:{s:2:\"id\";s:2:\"15\";s:4:\"slug\";s:7:\"akismet\";s:6:\"plugin\";s:19:\"akismet/akismet.php\";s:11:\"new_version\";s:5:\"3.1.7\";s:3:\"url\";s:38:\"https://wordpress.org/plugins/akismet/\";s:7:\"package\";s:56:\"https://downloads.wordpress.org/plugin/akismet.3.1.7.zip\";}}s:12:\"translations\";a:0:{}s:9:\"no_update\";a:1:{s:9:\"hello.php\";O:8:\"stdClass\":6:{s:2:\"id\";s:4:\"3564\";s:4:\"slug\";s:11:\"hello-dolly\";s:6:\"plugin\";s:9:\"hello.php\";s:11:\"new_version\";s:3:\"1.6\";s:3:\"url\";s:42:\"https://wordpress.org/plugins/hello-dolly/\";s:7:\"package\";s:58:\"https://downloads.wordpress.org/plugin/hello-dolly.1.6.zip\";}}}', 'yes'), ('186', 'auto_core_update_notified', 'a:4:{s:4:\"type\";s:7:\"success\";s:5:\"email\";s:12:\"admin@qq.com\";s:7:\"version\";s:5:\"4.3.2\";s:9:\"timestamp\";i:1454121415;}', 'yes');
	COMMIT;

	-- ----------------------------
	--  Table structure for `wp_postmeta`
	-- ----------------------------
	DROP TABLE IF EXISTS `wp_postmeta`;
	CREATE TABLE `wp_postmeta` (
	  `meta_id` bigint(20) unsigned NOT NULL AUTO_INCREMENT,
	  `post_id` bigint(20) unsigned NOT NULL DEFAULT '0',
	  `meta_key` varchar(255) COLLATE utf8mb4_unicode_ci DEFAULT NULL,
	  `meta_value` longtext COLLATE utf8mb4_unicode_ci,
	  PRIMARY KEY (`meta_id`),
	  KEY `post_id` (`post_id`),
	  KEY `meta_key` (`meta_key`(191))
	) ENGINE=InnoDB AUTO_INCREMENT=8 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

	-- ----------------------------
	--  Records of `wp_postmeta`
	-- ----------------------------
	BEGIN;
	INSERT INTO `wp_postmeta` VALUES ('1', '2', '_wp_page_template', 'default');
	COMMIT;

	-- ----------------------------
	--  Table structure for `wp_posts`
	-- ----------------------------
	DROP TABLE IF EXISTS `wp_posts`;
	CREATE TABLE `wp_posts` (
	  `ID` bigint(20) unsigned NOT NULL AUTO_INCREMENT,
	  `post_author` bigint(20) unsigned NOT NULL DEFAULT '0',
	  `post_date` datetime NOT NULL DEFAULT '0000-00-00 00:00:00',
	  `post_date_gmt` datetime NOT NULL DEFAULT '0000-00-00 00:00:00',
	  `post_content` longtext COLLATE utf8mb4_unicode_ci NOT NULL,
	  `post_title` text COLLATE utf8mb4_unicode_ci NOT NULL,
	  `post_excerpt` text COLLATE utf8mb4_unicode_ci NOT NULL,
	  `post_status` varchar(20) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT 'publish',
	  `comment_status` varchar(20) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT 'open',
	  `ping_status` varchar(20) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT 'open',
	  `post_password` varchar(20) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '',
	  `post_name` varchar(200) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '',
	  `to_ping` text COLLATE utf8mb4_unicode_ci NOT NULL,
	  `pinged` text COLLATE utf8mb4_unicode_ci NOT NULL,
	  `post_modified` datetime NOT NULL DEFAULT '0000-00-00 00:00:00',
	  `post_modified_gmt` datetime NOT NULL DEFAULT '0000-00-00 00:00:00',
	  `post_content_filtered` longtext COLLATE utf8mb4_unicode_ci NOT NULL,
	  `post_parent` bigint(20) unsigned NOT NULL DEFAULT '0',
	  `guid` varchar(255) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '',
	  `menu_order` int(11) NOT NULL DEFAULT '0',
	  `post_type` varchar(20) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT 'post',
	  `post_mime_type` varchar(100) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '',
	  `comment_count` bigint(20) NOT NULL DEFAULT '0',
	  PRIMARY KEY (`ID`),
	  KEY `post_name` (`post_name`(191)),
	  KEY `type_status_date` (`post_type`,`post_status`,`post_date`,`ID`),
	  KEY `post_parent` (`post_parent`),
	  KEY `post_author` (`post_author`)
	) ENGINE=InnoDB AUTO_INCREMENT=10 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

	-- ----------------------------
	--  Records of `wp_posts`
	-- ----------------------------
	BEGIN;
	INSERT INTO `wp_posts` VALUES ('1', '1', '2015-12-03 21:42:06', '2015-12-03 13:42:06', '欢迎使用WordPress。这是您的第一篇文章。编辑或删除它，然后开始写作吧！', '世界，您好！', '', 'publish', 'open', 'open', '', 'hello-world', '', '', '2015-12-03 21:42:06', '2015-12-03 13:42:06', '', '0', 'http://mysites/wordpress/?p=1', '0', 'post', '', '1'), ('2', '1', '2015-12-03 21:42:06', '2015-12-03 13:42:06', '这是一个范例页面。它和博客文章不同，因为它的页面位置是固定的，同时会显示于您的博客导航栏（大多数主题中）。大多数人会新增一个“关于”页面向访客介绍自己。它可能类似下面这样：\n\n<blockquote>我是一个很有趣的人，我创建了工厂和庄园。并且，顺便提一下，我的妻子也很好。</blockquote>\n\n……或下面这样：\n\n<blockquote>XYZ装置公司成立于1971年，公司成立以来，我们一直向市民提供高品质的装置。我们位于北京市，有超过2,000名员工，对北京市有着相当大的贡献。</blockquote>\n\n作为一个新的WordPress用户，您可以前往<a href=\"http://mysites/wordpress/wp-admin/\">您的仪表盘</a>删除这个页面，并建立属于您的全新内容。祝您使用愉快！', '示例页面', '', 'publish', 'closed', 'open', '', 'sample-page', '', '', '2015-12-03 21:42:06', '2015-12-03 13:42:06', '', '0', 'http://mysites/wordpress/?page_id=2', '0', 'page', '', '0');
	COMMIT;

	-- ----------------------------
	--  Table structure for `wp_term_relationships`
	-- ----------------------------
	DROP TABLE IF EXISTS `wp_term_relationships`;
	CREATE TABLE `wp_term_relationships` (
	  `object_id` bigint(20) unsigned NOT NULL DEFAULT '0',
	  `term_taxonomy_id` bigint(20) unsigned NOT NULL DEFAULT '0',
	  `term_order` int(11) NOT NULL DEFAULT '0',
	  PRIMARY KEY (`object_id`,`term_taxonomy_id`),
	  KEY `term_taxonomy_id` (`term_taxonomy_id`)
	) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

	-- ----------------------------
	--  Records of `wp_term_relationships`
	-- ----------------------------
	BEGIN;
	INSERT INTO `wp_term_relationships` VALUES ('1', '1', '0');
	COMMIT;

	-- ----------------------------
	--  Table structure for `wp_term_taxonomy`
	-- ----------------------------
	DROP TABLE IF EXISTS `wp_term_taxonomy`;
	CREATE TABLE `wp_term_taxonomy` (
	  `term_taxonomy_id` bigint(20) unsigned NOT NULL AUTO_INCREMENT,
	  `term_id` bigint(20) unsigned NOT NULL DEFAULT '0',
	  `taxonomy` varchar(32) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '',
	  `description` longtext COLLATE utf8mb4_unicode_ci NOT NULL,
	  `parent` bigint(20) unsigned NOT NULL DEFAULT '0',
	  `count` bigint(20) NOT NULL DEFAULT '0',
	  PRIMARY KEY (`term_taxonomy_id`),
	  UNIQUE KEY `term_id_taxonomy` (`term_id`,`taxonomy`),
	  KEY `taxonomy` (`taxonomy`)
	) ENGINE=InnoDB AUTO_INCREMENT=2 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

	-- ----------------------------
	--  Records of `wp_term_taxonomy`
	-- ----------------------------
	BEGIN;
	INSERT INTO `wp_term_taxonomy` VALUES ('1', '1', 'category', '', '0', '1');
	COMMIT;

	-- ----------------------------
	--  Table structure for `wp_terms`
	-- ----------------------------
	DROP TABLE IF EXISTS `wp_terms`;
	CREATE TABLE `wp_terms` (
	  `term_id` bigint(20) unsigned NOT NULL AUTO_INCREMENT,
	  `name` varchar(200) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '',
	  `slug` varchar(200) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '',
	  `term_group` bigint(10) NOT NULL DEFAULT '0',
	  PRIMARY KEY (`term_id`),
	  KEY `slug` (`slug`(191)),
	  KEY `name` (`name`(191))
	) ENGINE=InnoDB AUTO_INCREMENT=2 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

	-- ----------------------------
	--  Records of `wp_terms`
	-- ----------------------------
	BEGIN;
	INSERT INTO `wp_terms` VALUES ('1', '未分类', 'uncategorized', '0');
	COMMIT;

	-- ----------------------------
	--  Table structure for `wp_usermeta`
	-- ----------------------------
	DROP TABLE IF EXISTS `wp_usermeta`;
	CREATE TABLE `wp_usermeta` (
	  `umeta_id` bigint(20) unsigned NOT NULL AUTO_INCREMENT,
	  `user_id` bigint(20) unsigned NOT NULL DEFAULT '0',
	  `meta_key` varchar(255) COLLATE utf8mb4_unicode_ci DEFAULT NULL,
	  `meta_value` longtext COLLATE utf8mb4_unicode_ci,
	  PRIMARY KEY (`umeta_id`),
	  KEY `user_id` (`user_id`),
	  KEY `meta_key` (`meta_key`(191))
	) ENGINE=InnoDB AUTO_INCREMENT=34 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

	-- ----------------------------
	--  Records of `wp_usermeta`
	-- ----------------------------
	BEGIN;
	INSERT INTO `wp_usermeta` VALUES ('1', '1', 'nickname', 'admin'), ('2', '1', 'first_name', ''), ('3', '1', 'last_name', ''), ('4', '1', 'description', ''), ('5', '1', 'rich_editing', 'true'), ('6', '1', 'comment_shortcuts', 'false'), ('7', '1', 'admin_color', 'fresh'), ('8', '1', 'use_ssl', '0'), ('9', '1', 'show_admin_bar_front', 'true'), ('10', '1', 'wp_capabilities', 'a:1:{s:13:\"administrator\";b:1;}'), ('11', '1', 'wp_user_level', '10'), ('12', '1', 'dismissed_wp_pointers', ''), ('13', '1', 'show_welcome_panel', '1'), ('14', '1', 'session_tokens', 'a:1:{s:64:\"dcd08f44fba8b0edeb01fb7d155ec3cd354a46193f447241d5adf79ee06af359\";a:4:{s:10:\"expiration\";i:1454294205;s:2:\"ip\";s:9:\"127.0.0.1\";s:2:\"ua\";s:120:\"Mozilla/5.0 (Macintosh; Intel Mac OS X 10_10_5) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/48.0.2564.97 Safari/537.36\";s:5:\"login\";i:1454121405;}}'), ('15', '1', 'wp_dashboard_quick_press_last_post_id', '3'), ('16', '1', 'wp_user-settings', 'editor=tinymce&post_dfw=off&mfold=o'), ('17', '1', 'wp_user-settings-time', '1449498913'), ('18', '13', 'nickname', 'Hoodps'), ('19', '13', 'first_name', 'wangwei'), ('20', '13', 'last_name', 'wang'), ('21', '13', 'description', ''), ('22', '13', 'rich_editing', 'true'), ('23', '13', 'comment_shortcuts', 'false'), ('24', '13', 'admin_color', 'fresh'), ('25', '13', 'use_ssl', '0'), ('26', '13', 'show_admin_bar_front', 'true'), ('27', '13', 'wp_capabilities', 'a:1:{s:11:\"contributor\";b:1;}'), ('28', '13', 'wp_user_level', '1'), ('29', '13', 'dismissed_wp_pointers', ''), ('30', '13', 'session_tokens', 'a:1:{s:64:\"61506093f7d22685ad4e8ad785c43b0741ed37330142f6c7a121dfad8b89ed9d\";a:4:{s:10:\"expiration\";i:1449671684;s:2:\"ip\";s:9:\"127.0.0.1\";s:2:\"ua\";s:116:\"Mozilla/5.0 (Macintosh; Intel Mac OS X 10_10_5) AppleWebKit/601.2.7 (KHTML, like Gecko) Version/9.0.1 Safari/601.2.7\";s:5:\"login\";i:1449498884;}}'), ('31', '13', 'wp_user-settings', 'mfold=f'), ('32', '13', 'wp_user-settings-time', '1449498947'), ('33', '13', 'wp_dashboard_quick_press_last_post_id', '7');
	COMMIT;

	-- ----------------------------
	--  Table structure for `wp_users`
	-- ----------------------------
	DROP TABLE IF EXISTS `wp_users`;
	CREATE TABLE `wp_users` (
	  `ID` bigint(20) unsigned NOT NULL AUTO_INCREMENT,
	  `user_login` varchar(60) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '',
	  `user_pass` varchar(64) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '',
	  `user_nicename` varchar(50) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '',
	  `user_email` varchar(100) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '',
	  `user_url` varchar(100) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '',
	  `user_registered` datetime NOT NULL DEFAULT '0000-00-00 00:00:00',
	  `user_activation_key` varchar(60) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '',
	  `user_status` int(11) NOT NULL DEFAULT '0',
	  `display_name` varchar(250) COLLATE utf8mb4_unicode_ci NOT NULL DEFAULT '',
	  PRIMARY KEY (`ID`),
	  KEY `user_login_key` (`user_login`),
	  KEY `user_nicename` (`user_nicename`)
	) ENGINE=InnoDB AUTO_INCREMENT=14 DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci;

	-- ----------------------------
	--  Records of `wp_users`
	-- ----------------------------
	BEGIN;
	INSERT INTO `wp_users` VALUES ('1', 'admin', '$P$BcoDHfEHZI8fL7h7s4Wc9HBK9Wj3O50', 'admin', 'admin@qq.com', '', '2015-12-03 13:42:06', '', '0', 'admin'), ('2', '837634', '21232f297a57a5a743894a0e4a801fc3', 'test', 'test@qq.com', '', '2015-12-31 00:00:00', '', '0', ''), ('3', 'test1', 'd4b2758da0205c1e0aa9512cd188002a', '安慰', '27186434@qq.com', 'www.hoodps.com', '2015-04-20 10:00:00', '', '1', 'sdfkj'), ('10', 'test4', 'd4b2758da0205c1e0aa9512cd188002a', '安慰', '27186434@qq.com', 'www.hoodps.com', '2015-04-20 10:00:00', '', '1', 'sdfkj'), ('12', '345346', 'd4b2758da0205c1e0aa9512cd188002a', '安慰', '27186434@qq.com', 'www.hoodps.com', '2015-04-20 10:00:00', '', '1', 'sdfkj'), ('13', 'Hoodps', '$P$BrGvy4rNHnJK/MuFSstaJplL/fn8iH1', 'hoodps', '2345678@qq.com', 'http://hoodps.com', '2015-12-07 14:32:13', '1449498734:$P$BPI2z7TeyiCdTja7/1mP.d3jcARQum1', '0', 'wang, wangwei');
	COMMIT;

	SET FOREIGN_KEY_CHECKS = 1;
