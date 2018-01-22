<!DOCTYPE html>
<html lang="ja"><head>
<meta charset="UTF-8" />
<meta http-equiv="X-UA-Compatible" content="IE=Edge" />
</head>
<body>
<h1>Darwin Cydia Repository Manager (DCRM) Pro Guide</h1>
<h2>DCRM 1.7 Pro 帮助手册 - 简体中文</h2>
<h3>欢迎</h3>
<div class="lv">
	<p>
		欢迎使用 Darwin Cydia Repository Manager Pro（下称“DCRM”或“WEIPDCRM”），DCRM 是一个适用于 Saurik 的 Cydia™ 客户端的源管理器。<br/>
		本软件基于 tibounise 的 "<a href="https://github.com/tibounise/DCRM">DCRM</a>" 项目重新设计，我们添加了超过95%的新功能使搭建的源变得更棒。
	</p>
	<p>
		使用DCRM可以搭建功能强大的 Cydia 个人源，让您省却对后台技术的担心，集中精力做好内容。
	</p>
	<p>
		WEIPDCRM 是开源免费软件，您可以在自由软件联盟发布的 GNU Affero 通用公共许可协议的约束下对其进行再发布及修改。<br/>
		协议详情请参阅：<a href="http://www.gnu.org/licenses/agpl-3.0.html">http://www.gnu.org/licenses/agpl-3.0.html</a>
	</p>
	<p>
		若您需要帮助，可以详细浏览本帮助文档，或者通过访问 WEIPDCRM 在 Github 上的<b><a href="https://github.com/Lessica/WEIPDCRM">开源主页</a></b>（英文）联系我们。祝您使用愉快！
	</p>
</div>
<h3>环境部署</h3>
<div class="lv">
	<h4>环境支持</h4>
	<ol>
		<li><strong>操作系统支持</strong><br/>类 Unix 操作系统(<b>推荐</b>) 或 Windows</li>
		<li><strong>FastCGI 支持</strong><br/>PHP >= 5.3<br/><i>需要预编译的 GZIP, BZIP2, GD, MYSQL 扩展 ，支持在 Safe Mode 下运行（如果不支持某项扩展，只需注释掉相关行即可。）</i></li>
		<li><strong>网页服务端支持</strong><br/>Apache >= 2.4.7, Nginx >= 1.0.11 (Rewrite: include dcrm.conf;), Lighttpd >= 1.0 (Rewrite: include dcrm_lighttpd.conf;)</li>
		<li><strong>数据库支持</strong><br/>MySQL 或 MariaDB</li>
	</ol>
</div>
<div class="lv">
	<h4>安装步骤</h4>
	<ul>
		<li>自动安装：配置好上文中的服务器环境，将 main 目录中的所有文件上传到网站目录</li>
		<li>确保程序根目录下有读取、写入权限</li>
		<li>如果您使用的 Web 服务器不是 Apache，将需要您有一定的高级操作知识和能力。您需要视情况启用相应的 Rewrite 规则。</li>
		<li>访问 http://{YOUR_REPO_URL} 自动跳转或直接访问 http://{YOUR_REPO_URL}/install 进行数据库配置</li>
	</ul>
	<br/>
	如果您有特殊的要求并有一定的高级操作知识和能力，您可以修改 ./system/config/connect.inc.default.php 手动配置数据库：
	<div class="box" style="color:#444;">
		1. 将 DCRM_CON_SERVER 设为 MYSQL 数据库服务器的完整地址<br/>
		2. 将 DCRM_CON_SERVER_PORT 设为 MYSQL 数据库服务器端口<br/>
		3. 将 DCRM_CON_DATABASE 设为已经建立完成的数据库名<br/>
		4. 将 DCRM_CON_USERNAME, DCRM_CON_PASSWORD 设为可访问该数据库并拥有足够权限的用户名和密码<br/>
		5. 如果您需要保持数据库连接，请将 DCRM_CON_PCONNECT 设为 True<br/>
		6. 我们不推荐手动初始化程序所需要的数据库，请访问 ./install/setup-install.php，进行数据库的安装
	</div>
</div>
<div class="lv">
	<h4>升级步骤</h4>
	1. 将所有文件上传或替换到网站目录<br/>
	2. 访问源的任意页面即可自动更新
</div>

<h3 class="public_html">使用说明</h3>
<div class="lv">
	<h4>首次使用</h4>
	<div class="lv">
		请进入右上角的设置以及左侧的源信息设置进行初期配置。
	</div>
	<h4>软件包功能</h4>
	<div class="lv">
		<ul>
			<li>
				<strong>上传软件包</strong>
				<div>您可以通过网页以及 FTP 将软件包上传到 upload 目录下，以便导入。</div>
			</li>
			<li>
				<strong>导入软件包</strong>
				<div>您可以将 upload 目录下的软件包导入到数据库。</div>
			</li>
			<li>
				<strong>升级导入</strong>
				<div>
					如果您是对软件包进行升级导入操作，导入时会出现操作提示。
					<div style="margin:0.5em 0em 0.5em 2em;">
						· 继承并替换是指新软件包继续使用原软件包的信息（除版本号外），并将原软件包隐藏；<br/>
						· 直接替换是指将原软件包隐藏；<br/>
						· 添加条目是指忽略原软件包的存在；
					</div>
				</div>
			</li>
			<li>
				<strong>管理软件包</strong>
				<div>
					您可以：<br/>
					· 控制软件包的显示、隐藏；<br/>
					· 搜索、寻找并选择编辑或删除软件包；<br/>
					· 查看软件包概况；</div>
			</li>
			<li>
				<strong>显示或隐藏软件包</strong>
				<div>
					新导入的软件包默认是隐藏的（包括升级导入），隐藏状态表示为 <span style="color: green;">绿色</span>，显示状态表示为 <span style="color: blue;">蓝色</span>；<br/>
					* 若要更改状态，单击它们前方的按钮，在左侧点击“显示软件包”或“隐藏软件包”。
				</div>
			</li>
			<li>
				<strong>查看软件包</strong>
				<div>您可以查看该软件包中所包含的控制信息，以及管理系统的附加信息。</div>
			</li>
			<li>
				<strong>编辑软件包</strong>
				<div>
					· 常规编辑提供了常见信息的修改与保存；<br/>
					· 高级编辑提供了更多字段的修改，这需要您对 Debian 软件包有一定的高级操作知识和能力。
				</div>
			</li>
			<li>
				<strong>查找软件包</strong>
				<div>您可以按照多个字段查找软件包，暂时不能使用通配符和正则表达式。</div>
			</li>
			<li>
				<strong>为软件包绑定UDID</strong>
				<div>您为软件包绑定设备UDID，详细请参阅《<a href="#UDID">UDID 绑定</a>》一节。</div>
			</li>
		</ul>
	</div>
	<h4>分类管理</h4>
	<div class="lv">
		您可以添加，删除，查看软件包分类，并在编辑软件包的时候为其选择一个已配置的分类。
	</div>
	<h4>图标管理</h4>
	<div class="lv">
		您可以上传源图标，分类图标，并在分类管理中生成图标包。
	</div>
	<h4>运行状态</h4>
	<div class="lv">
		您可以查看数据库状态、系统信息、总下载量与软件包数量等信息。
	</div>
	<h4>关于程序</h4>
	<div class="lv">
		您可以查看 DCRM 的开发人员名单、翻译名单、感谢名单等。
	</div>
	<h4>刷新列表</h4>
	<div class="lv">
		刷新列表前您必须将欲显示的软件包置于 显示 状态；<br/>
		单击此按钮将生成 Packages, Packages.gz, Packages.bz2 列表文件并计算 MD5sum 与 Size。
	</div>
</div>
<h3 id="UDID">UDID 绑定<sup>*</sup></h3>
<div class="lv">
	<h4>简介</h4>
	<div class="lv">
		DCRM 为您提供了软件包 UDID 绑定功能，使用该功能您可以很简单地保护您的个人软件包<sup>+</sup>。<br/>
		该功能通过检测请求设备的 UDID 来阻挡或允许下载软件包。<br/>
		<p style="color:#444;">
			* UDID 绑定为1.6.15.3.26新增功能。<br/>
			+ 本功能推荐用于个人开发者的软件包内测。
		</p>
	</div>
</div>
<div class="lv">
	<h4>使用说明</h4>
	<div class="lv">
		<ul>
			<li>
				<strong>为软件包启用该功能</strong>
				<div>
					您需要在您想启用的软件包中的常规编辑界面中启用 <b>保护</b> 选项，系统将会自动为该软件包添加 <code>cydia::commercial</code> 标签。您也可以自行在软件包中添加该标签以启用此功能。<br/>
					注意：修改该选项后您需要写入软件包才可正式生效。
				</div>
			</li>
			<li>
				<strong>等级设置</strong>
				<div>
					在 DCRM 的判断逻辑中，等级的优先度高于 UDID绑定。<br/>
					举例来说，您想让一个设备拥有特殊的下载权限，您可以在UDID管理页中设置该设备的等级。此时，只要该设备下载的软件包等级低于该设备的等级，则该设备可以无视UDID绑定设置下载该软件包。
				</div>
			</li>
			<li>
				<strong>管理等级</strong>
				<div>
					管理UDID 页面中的 管理等级 为<b>预留接口</b>，目前您可以为等级添加备注。
				</div>
			</li>
		</ul>
	</div>
</div>
<div class="lv">
	<h4>其它说明</h4>
	<div class="lv">
		我们为受保护软件包在软件包详情页添加了状态显示，但由于Cydia的限制，可能会出现在已绑定的设备上显示的状态不正确。但下载软件包时 UDID 检测是正常工作的，在找到更好的替代方案前请见谅。
	</div>
</div>
<h3>为 Release 文件签名</h3>
<div class="lv">
	<h4>简介</h4>
	DCRM 可以使用 GPG 工具对 Release 文件进行签名，签名后可以使 Cydia 检验源的文件在传输过程中是否被篡改，可以提高一定的安全性。<br/>
	既然您选择为您的 Release 文件进行签名，这代表您对软件源的安全性有一定要求，也代表您有一定的高级操作知识和能力，如果您认可了这两点，请继续阅读。
</div>
<div class="lv">
	<h4>环境要求</h4>
	<ol>
		<li>Windows 或 类Unix操作系统</li>
		<li>处于 non-Safe Mode （非安全模式）下的 PHP 环境，且具有运行 GPG 命令的权限，GPG 工具可以通过各种方式获取。</li>
	</ol>
</div>
<div class="lv">
	<h4>操作</h4>
	<div class="lv">
		请先阅读 how_to_host_cydia_repo.pdf 中《用于签名 Release 的密匙》章节，为您的软件源生成一个密钥，并制作相关软件源验证包，导出私钥。<br/>
		在服务器上导入该私钥，并修改 ./system/config/gnupg.inc.php 中的相关参数：
		<div class="pbox" style="color:#444;">
			1. 将 DCRM_GNUPG_ENABLED 设为 1；<br/>
			2. 将 DCRM_GNUPG_PATH 设为 gpg 命令的路径；<br/>
			3. 将 DCRM_GNUPG_NAME 设为您私钥的名称；<br/>
			4. 将 DCRM_GNUPG_PASS 设为您私钥的口令；
		</div>
		进行源信息设置，并刷新列表，在用户端安装软件源验证包即可完成。<br/>
		每次刷新列表，签名数据会自动更新。
	</div>
</div>
<h3>疑难解答</h3>
<div class="lv">
	<ul>
		<li>
			<strong><em>为什么保存编辑以后还需要写入软件包？</em></strong>
			<div style="margin:0.5em 0em 0.5em 0.5em;">
				这是由于 Cydia™ 要求 Packages 列表与软件包中的部分字段必须相同；<br/>
				通常，您修改标题，作者，提供者，保证人，主页，预览页和描述的时候无需写入软件包。
			</div>
		</li>
		<li>
			<strong><em>为什么需要手动刷新列表？</em></strong>
			<div style="margin:0.5em 0em 0.5em 0.5em;">每次编辑后自动刷新可能会导致软件源的不稳定，所以需要您在所有更改结束后手动刷新列表；</div>
		</li>
		<li>
			<strong><em>缓存是如何产生的？</em></strong>
			<div style="margin:0.5em 0em 0.5em 0.5em;">导入、写入软件包、生成图标包等均会产生临时缓存，随时可以清理。</div>
		</li>
		<li>
			<strong><em>为什么我不能通过普通浏览器或 Cyder 拉取软件源列表和软件包？ </em></strong>
			<div style="margin:0.5em 0em 0.5em 0.5em;">
				这是因为 DCRM 具有防盗链功能，只允许 Cydia™ 的访问请求；<br/>
				如果您想关闭此功能，只需在设置中关闭防盗链功能。
			</div>
		</li>
		<li>
			<strong><em>我该如何在描述中使用换行符？</em></strong>
			<div style="margin:0.5em 0em 0.5em 0.5em;">Cydia™ 支持使用 HTML 中的换行标记。</div>
		</li>
		<li>
			<strong><em>DCRM 的安全性如何？ </em></strong>
			<div style="margin:0.5em 0em 0.5em 0.5em;">
				DCRM 并不提供商业级别的安全保障，后台登录采用了会话机制，请确保您的会话未被监听；<br/>
				后台密码采用 SHA1 摘要算法存储并对比；<br/>
				我们推荐您开启 SSL 以保证访问的安全。（注意：开启 SSL 可能会增加服务器负载。）<br/>
				请确保做好了服务器的防护工作，例如：将 PHP 运行于安全模式、不允许外网访问 MySQL 服务器等。
			</div>
		</li>
	</ul>
</div>
<h3>更多信息</h3>
<div class="lv">
	<h4>编码</h4>
	<div>请使用支持 utf8_general_ci 编码的 MYSQL 数据库，DCRM 所有部分均使用 UTF-8 编码。</div>
	<h4>其它</h4>
	<div>
		<p>
			您可以访问 WEIPDCRM 在 Github 上的开源主页以反馈问题、建议功能、查看更新等：<br/>
			<a href="https://github.com/82Flex/WEIPDCRM">https://github.com/82Flex/WEIPDCRM</a> （英文）
		</p>
		<p>
			本帮助页重制：<a href="http://weibo.com/Hintay">@Hintay</a>
		</p>
	</div>
</div>

<h3></h3>
<div class="lv"></div>
<div>
	<div align="center">Copyright&copy; 2015-2016 <strong>i_82</strong> &amp; <strong>Hintay</strong>. All rights reserved.</div>
</div>
</body></html>
