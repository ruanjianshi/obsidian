<%*
// 定义选中的文本内容
let content = tp.file.selection();
// 定义 callout 选项列表 - 精简分类，避免重复
let list = {
  "💎 重点": { 
    style: "important", 
    title: "重点核心",
    color: "#fff0f6",
    borderColor: "#eb2f96",
    emoji: "💎"
  },
  "💡 观点": { 
    style: "idea", 
    title: "核心观点", 
    color: "#f6ffed", 
    borderColor: "#52c41a",
    emoji: "💡"
  },
  "📚 知识": { 
    style: "knowledge", 
    title: "知识要点", 
    color: "#f0f5ff", 
    borderColor: "#2f54eb",
    emoji: "📚"
  },
  "⚡ 技巧": { 
    style: "tip", 
    title: "实用技巧", 
    color: "#fcffe6", 
    borderColor: "#a0d911",
    emoji: "⚡"
  },
  "⚠️ 注意": { 
    style: "caution", 
    title: "注意事项", 
    color: "#fff7e6", 
    borderColor: "#fa8c16",
    emoji: "⚠️"
  },
  "❓ 问题": { 
    style: "question", 
    title: "思考问题", 
    color: "#f6ffed", 
    borderColor: "#73d13d",
    emoji: "❓"
  },
  "✅ 总结": { 
    style: "summary", 
    title: "内容总结", 
    color: "#f9f0ff", 
    borderColor: "#722ed1",
    emoji: "✅"
  },
  "🔗 参考": { 
    style: "reference", 
    title: "参考资料", 
    color: "#e6f7ff", 
    borderColor: "#1890ff",
    emoji: "🔗"
  }
};

// 生成提示模式并返回用户的输入
let keys = Object.keys(list);
let selectedKey = await tp.system.suggester(keys, keys);

if (!selectedKey) return; // 用户取消选择时退出

// 获取选中的配置
let config = list[selectedKey];

// 处理内容
let result = "";
if (content && content.trim().length > 0) {
  // 有选中内容时，处理每一行
  let processedLines = content.split("\n").map(line => {
    if (line.trim() === "") return ">"; // 空行处理
    return "> " + line;
  });
  result = processedLines.join("\n");
} else {
  // 没有选中内容时，创建空的callout
  result = ">";
}

// 构建最终的callout，使用emoji作为图标
let finalCallout = `> [!${config.style}]+ ${config.emoji} ${config.title}\n${result}`;

// 返回结果
return finalCallout;
%>

<style>
/* 基础Callout样式 */
.callout {
  border-radius: 8px;
  border-left-width: 4px;
  margin: 1em 0;
  transition: all 0.2s ease;
}

.callout:hover {
  transform: translateY(-1px);
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
}

.callout-title {
  font-weight: 600;
  border-bottom: 1px solid rgba(0, 0, 0, 0.05);
  padding-bottom: 8px;
  margin-bottom: 8px;
}

/* 重点核心样式 */
.callout[data-callout="important"] {
  background: linear-gradient(135deg, #fff0f6 0%, #fff9f0 100%);
  border-color: #eb2f96;
}

.callout[data-callout="important"] .callout-title {
  color: #c41d7f;
}

/* 核心观点样式 */
.callout[data-callout="idea"] {
  background: linear-gradient(135deg, #f6ffed 0%, #f0fff9 100%);
  border-color: #52c41a;
}

.callout[data-callout="idea"] .callout-title {
  color: #389e0d;
}

/* 知识要点样式 */
.callout[data-callout="knowledge"] {
  background: linear-gradient(135deg, #f0f5ff 0%, #f0f8ff 100%);
  border-color: #2f54eb;
}

.callout[data-callout="knowledge"] .callout-title {
  color: #1d39c4;
}

/* 实用技巧样式 */
.callout[data-callout="tip"] {
  background: linear-gradient(135deg, #fcffe6 0%, #feffe6 100%);
  border-color: #a0d911;
}

.callout[data-callout="tip"] .callout-title {
  color: #7cb305;
}

/* 注意事项样式 */
.callout[data-callout="caution"] {
  background: linear-gradient(135deg, #fff7e6 0%, #fff2e8 100%);
  border-color: #fa8c16;
}

.callout[data-callout="caution"] .callout-title {
  color: #d46b08;
}

/* 思考问题样式 */
.callout[data-callout="question"] {
  background: linear-gradient(135deg, #f6ffed 0%, #f0fffd 100%);
  border-color: #73d13d;
}

.callout[data-callout="question"] .callout-title {
  color: #389e0d;
}

/* 内容总结样式 */
.callout[data-callout="summary"] {
  background: linear-gradient(135deg, #f9f0ff 0%, #f0f4ff 100%);
  border-color: #722ed1;
}

.callout[data-callout="summary"] .callout-title {
  color: #531dab;
}

/* 参考资料样式 */
.callout[data-callout="reference"] {
  background: linear-gradient(135deg, #e6f7ff 0%, #f0faff 100%);
  border-color: #1890ff;
}

.callout[data-callout="reference"] .callout-title {
  color: #096dd9;
}
</style>