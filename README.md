Flare 链上信息平台
一个基于 Flare 公链的完全去中心化信息发布与评论平台，灵感来自 58 同城。
所有信息和评论永久上链，无需中心化服务器，任何钱包用户均可自由发布。

✨ 功能特点
🔗 完全链上存储：所有信息、评论均存储在 Flare 区块链上，不可篡改，永久可查。

👛 钱包登录：支持 Rabby、OKX Wallet、MetaMask 等标准钱包，连接后即可发布信息或评论。

👁️ 无需登录即可浏览：任何人都可以查看所有已发布的信息和评论，无需连接钱包。

📝 信息发布：标题最多 200 汉字，内容最多 500 汉字，可选分类（招聘/房产/二手/服务/其他）。

💬 评论功能：任何登录用户可在信息下方添加评论，每条评论最多 200 汉字。

🎨 美观界面：毛玻璃效果、卡片悬浮、响应式设计，适配 PC 与移动端。

⚡ 实时数据：通过合约只读调用实时获取最新信息。

📁 项目结构
text
.
├── InfoBoard.sol          # 智能合约源代码
├── index.html             # 前端单页面（HTML/JS/CSS）
└── README.md              # 项目说明文档
🧱 技术栈
区块链：Flare 主网

智能合约：Solidity ^0.8.0

前端：HTML5 + CSS3 + JavaScript (ES6)

Web3 库：ethers.js v5.7.2

钱包：Rabby / OKX Wallet / MetaMask 等（支持 EIP-1193）

🚀 快速开始
1. 体验线上平台（已部署）
直接访问线上地址（例如通过 EdgeOne Pages 或 GitHub Pages 部署后的链接），即可使用。
若尚未部署，可参考下文“部署指南”。

2. 本地运行
将 index.html 下载到本地，用现代浏览器（Chrome、Firefox、Edge）打开即可。

注意：本地打开时，ethers.js 需从 CDN 加载，确保网络畅通；钱包连接需要浏览器安装钱包插件。

3. 连接钱包并发布信息
点击右上角“连接钱包”，选择 Rabby/OKX 等，确认切换至 Flare 主网（如未自动切换，请手动添加网络）。

连接成功后，左侧发布表单即可填写标题、内容、分类，点击“发布信息”完成上链。

右侧点击任意信息条目可查看详情和评论，连接钱包后可在下方发表评论。

📦 部署指南
智能合约部署
打开 Remix IDE

新建文件 InfoBoard.sol，粘贴合约源代码

编译（Solidity 0.8.x）

环境选择 “Injected Provider - MetaMask”，确保钱包已切换至 Flare 主网

点击部署，确认交易

部署成功后记录合约地址（例如：0x1bc6D5dbD58d2d6F4905dbe098120fDcC250f4a7）

前端部署
下载 index.html，或从本仓库获取。

修改 index.html 中的 CONTRACT_ADDRESS 为你的实际合约地址。

将文件部署到任意静态托管平台，推荐：

EdgeOne Pages Drop（最简单，拖拽即可）

GitHub Pages

Netlify

Vercel

部署后即可通过生成的 URL 访问平台。

📜 合约接口说明
枚举 Category
solidity
enum Category { Job, House, SecondHand, Service, Other }
结构体 Post
solidity
struct Post {
    address publisher;
    string title;
    string content;
    Category category;
    uint256 timestamp;
}
结构体 Comment
solidity
struct Comment {
    address commenter;
    string content;
    uint256 timestamp;
}
主要函数
函数	参数	说明
createPost	string title, string content, Category category	发布信息，触发 PostCreated 事件
addComment	uint256 postId, string content	添加评论，触发 CommentAdded 事件
getAllPostIds	无	返回所有信息 ID 数组
getPostsBatch	uint256[] ids	批量获取信息详情
getCommentsForPost	uint256 postId	获取某条信息的所有评论
getPostCount	无	返回信息总数
事件
PostCreated(uint256 indexed postId, address indexed publisher, Category category, string title)

CommentAdded(uint256 indexed postId, address indexed commenter, string content)

⚙️ 配置说明
在 index.html 中可修改以下常量：

javascript
const CONTRACT_ADDRESS = "0x1bc6D5dbD58d2d6F4905dbe098120fDcC250f4a7"; // 你的合约地址
const FLARE_RPC = "https://flare-api.flare.network/ext/C/rpc";   // Flare 主网 RPC
const FLARE_CHAIN_ID = 14;                                        // Flare 主网链 ID
📝 注意事项
Gas 费：发布信息和评论需要消耗少量 FLR 作为 Gas 费，请确保钱包有足够余额。

字符限制：标题最多 200 汉字（600 字节），内容最多 500 汉字（1500 字节），评论最多 200 汉字（600 字节）。
合约严格校验字节长度，输入 emoji 等特殊字符可能占用更多字节，前端计数器仅作参考。

网络切换：首次连接钱包时，前端会尝试自动切换至 Flare 主网，若失败请手动添加网络。

数据不可修改：所有信息一旦上链即永久保存，无法删除或修改。请谨慎发布。

安全提示：本平台完全开源，所有交易均通过钱包确认，请勿向他人泄露私钥。

🤝 贡献指南
欢迎提交 Issue 或 Pull Request。
如需新增功能（如点赞、修改信息等），请先创建 Issue 讨论。

📄 开源协议
MIT License

让信息永久留存，让交流自由无界。


