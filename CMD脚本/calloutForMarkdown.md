<%*
// 获取选中的文本
let selectedText = tp.file.selection();

// 定义常用Markdown命令选项
let list = {
  "📋 代码块": {
    template: async (text) => {
      let languages = ["javascript","dataview","c","c++", "python", "java", "html", "css", "typescript", "bash", "sql", "json", "markdown"];
      let languageChoice = await tp.system.suggester(languages, languages);
      return `\`\`\`${languageChoice || "text"}\n${text || "// 在这里编写代码"}\n\`\`\`\n`;
    }
  },
  "📊 表格": {
    template: (text) => {
      return `| 列1 | 列2 | 列3 |\n|-----|-----|-----|\n| 内容 | 内容 | 内容 |\n| 内容 | 内容 | 内容 |\n`;
    }
  },
  "📝 数学公式": {
    template: (text) => {
      return text ? `$$\n${text}\n$$\n` : `$$\n\\begin{equation}\n你的公式在这里\n\\end{equation}\n$$\n`;
    }
  },
  "🔗 链接": {
    template: async (text) => {
      let linkText = text || await tp.system.prompt("请输入链接名称：", "示例链接");
      let url = await tp.system.prompt("请输入链接地址：", "https://example.com");
      // 处理多行链接文本
      if (linkText.includes('\n')) {
        let lines = linkText.split('\n').filter(line => line.trim());
        let linkedLines = lines.map(line => `[${line}](${url})`).join('  \n');
        return linkedLines + '\n';
      }
      return `[${linkText}](${url})\n`;
    }
  },
  "✅ 任务列表": {
    template: (text) => {
      if (text) {
        let lines = text.split('\n').filter(line => line.trim());
        let tasks = lines.map(line => `- [ ] ${line.trim()}`).join('\n');
        return tasks + '\n';
      }
      return `- [ ] 待办事项1\n- [ ] 待办事项2\n- [x] 已完成事项\n`;
    }
  },
  "🔖 引用块": {
    template: (text) => {
      if (text) {
        let lines = text.split('\n').map(line => line.trim()).filter(line => line);
        let quoteLines = lines.map(line => `> ${line}`).join('\n');
        return quoteLines + '\n';
      }
      return `> 这里是引用内容\n> 可以多行显示\n`;
    }
  },
  "📏 分割线": {
    template: (text) => {
      return `---\n`;
    }
  },
  "🎯 高亮文本": {
    template: (text) => {
      if (text && text.includes('\n')) {
        let lines = text.split('\n').filter(line => line.trim());
        let highlightedLines = lines.map(line => `==${line}==`).join('  \n');
        return highlightedLines + '\n';
      }
      return text ? `==${text}==\n` : `==高亮文本==\n`;
    }
  },
  "💬 行内代码": {
    template: (text) => {
      if (text && text.includes('\n')) {
        let lines = text.split('\n').filter(line => line.trim());
        let codeLines = lines.map(line => `\`${line}\``).join('  \n');
        return codeLines + '\n';
      }
      return text ? `\`${text}\`\n` : `\`行内代码\`\n`;
    }
  },
  "🌟 粗体文本": {
    template: (text) => {
      if (text && text.includes('\n')) {
        let lines = text.split('\n').filter(line => line.trim());
        let boldLines = lines.map(line => `**${line}**`).join('  \n');
        return boldLines + '\n';
      }
      return text ? `**${text}**\n` : `**粗体文本**\n`;
    }
  },
  "✨ 斜体文本": {
    template: (text) => {
      if (text && text.includes('\n')) {
        let lines = text.split('\n').filter(line => line.trim());
        let italicLines = lines.map(line => `*${line}*`).join('  \n');
        return italicLines + '\n';
      }
      return text ? `*${text}*\n` : `*斜体文本*\n`;
    }
  },
  "🚫 删除线": {
    template: (text) => {
      if (text && text.includes('\n')) {
        let lines = text.split('\n').filter(line => line.trim());
        let strikeLines = lines.map(line => `~~${line}~~`).join('  \n');
        return strikeLines + '\n';
      }
      return text ? `~~${text}~~\n` : `~~删除线文本~~\n`;
    }
  },
  "🔠 上标": {
    template: (text) => {
      if (text && text.includes('\n')) {
        let lines = text.split('\n').filter(line => line.trim());
        let supLines = lines.map(line => `<sup>${line}</sup>`).join('  \n');
        return supLines + '\n';
      }
      return text ? `<sup>${text}</sup>\n` : `<sup>上标</sup>\n`;
    }
  },
  "🔡 下标": {
    template: (text) => {
      if (text && text.includes('\n')) {
        let lines = text.split('\n').filter(line => line.trim());
        let subLines = lines.map(line => `<sub>${line}</sub>`).join('  \n');
        return subLines + '\n';
      }
      return text ? `<sub>${text}</sub>\n` : `<sub>下标</sub>\n`;
    }
  },
  "🔴 红色文本": {
    template: (text) => {
      if (text && text.includes('\n')) {
        let lines = text.split('\n').filter(line => line.trim());
        let coloredLines = lines.map(line => `<span style="color: #ff6b6b">${line}</span>`).join('  \n');
        return coloredLines + '\n';
      }
      return text ? `<span style="color: #ff6b6b">${text}</span>\n` : `<span style="color: #ff6b6b">红色文本</span>\n`;
    }
  },
  "🔵 蓝色文本": {
    template: (text) => {
      if (text && text.includes('\n')) {
        let lines = text.split('\n').filter(line => line.trim());
        let coloredLines = lines.map(line => `<span style="color: #4dabf7">${line}</span>`).join('  \n');
        return coloredLines + '\n';
      }
      return text ? `<span style="color: #4dabf7">${text}</span>\n` : `<span style="color: #4dabf7">蓝色文本</span>\n`;
    }
  },
  "🟢 绿色文本": {
    template: (text) => {
      if (text && text.includes('\n')) {
        let lines = text.split('\n').filter(line => line.trim());
        let coloredLines = lines.map(line => `<span style="color: #51cf66">${line}</span>`).join('  \n');
        return coloredLines + '\n';
      }
      return text ? `<span style="color: #51cf66">${text}</span>\n` : `<span style="color: #51cf66">绿色文本</span>\n`;
    }
  },
  "🟡 黄色文本": {
    template: (text) => {
      if (text && text.includes('\n')) {
        let lines = text.split('\n').filter(line => line.trim());
        let coloredLines = lines.map(line => `<span style="color: #ffd43b">${line}</span>`).join('  \n');
        return coloredLines + '\n';
      }
      return text ? `<span style="color: #ffd43b">${text}</span>\n` : `<span style="color: #ffd43b">黄色文本</span>\n`;
    }
  },
  "🟣 紫色文本": {
    template: (text) => {
      if (text && text.includes('\n')) {
        let lines = text.split('\n').filter(line => line.trim());
        let coloredLines = lines.map(line => `<span style="color: #cc5de8">${line}</span>`).join('  \n');
        return coloredLines + '\n';
      }
      return text ? `<span style="color: #cc5de8">${text}</span>\n` : `<span style="color: #cc5de8">紫色文本</span>\n`;
    }
  },
  "🔶 橙色文本": {
    template: (text) => {
      if (text && text.includes('\n')) {
        let lines = text.split('\n').filter(line => line.trim());
        let coloredLines = lines.map(line => `<span style="color: #ff922b">${line}</span>`).join('  \n');
        return coloredLines + '\n';
      }
      return text ? `<span style="color: #ff922b">${text}</span>\n` : `<span style="color: #ff922b">橙色文本</span>\n`;
    }
  },
  "👣 脚注": {
    template: (text) => {
      if (text) {
        if (text.includes('\n')) {
          let lines = text.split('\n').filter(line => line.trim());
          let footnotes = lines.map((line, index) => `${line}[^${index + 1}]`).join('  \n');
          let footnoteDefs = lines.map((line, index) => `[^${index + 1}]: 脚注说明 ${index + 1}`).join('\n');
          return footnotes + '\n\n' + footnoteDefs + '\n';
        }
        return `${text}[^1]\n\n[^1]: 这里是脚注的详细说明。\n`;
      }
      return `在这里添加内容[^1]\n\n[^1]: 这里是脚注的详细说明。\n`;
    }
  },
  "❓ 折叠内容": {
    template: async (text) => {
      let title = await tp.system.prompt("请输入折叠标题：", "点击展开");
      return `<details>\n<summary>${title}</summary>\n\n${text || "这里是被折叠的内容"}\n\n</details>\n`;
    }
  },
  "🔄 注释": {
    template: (text) => {
      if (text && text.includes('\n')) {
        let lines = text.split('\n').filter(line => line.trim());
        let commentLines = lines.map(line => `%% ${line} %%`).join('\n');
        return commentLines + '\n';
      }
      return text ? `%% ${text} %%\n` : `%% 这是注释，不会在预览中显示 %%\n`;
    }
  },
  "📅 时间戳": {
    template: (text) => {
      let prefix = text ? text : "创建时间";
      return `**${prefix}：** ${tp.date.now()}\n`;
    }
  },
  "🔤 定义列表": {
    template: (text) => {
      if (text) {
        let lines = text.split('\n').filter(line => line.trim());
        let definitions = lines.map((line, index) => `${line}\n: 定义${index + 1}`).join('\n\n');
        return definitions + '\n';
      }
      return `术语1\n: 定义1\n\n术语2  \n: 定义2\n`;
    }
  },
  "🎨 自定义颜色": {
    template: async (text) => {
      let content = text || await tp.system.prompt("请输入文本内容：", "自定义颜色文本");
      let color = await tp.system.prompt("请输入颜色（如：#ff6b6b, blue, red）：", "#ff6b6b");
      if (content.includes('\n')) {
        let lines = content.split('\n').filter(line => line.trim());
        let coloredLines = lines.map(line => `<span style="color: ${color}">${line}</span>`).join('  \n');
        return coloredLines + '\n';
      }
      return `<span style="color: ${color}">${content}</span>\n`;
    }
  }
};

// 生成提示模式并返回用户的输入
let keys = Object.keys(list);
let selectedKey = await tp.system.suggester(keys, keys);

if (!selectedKey) return; // 用户取消选择时退出

// 执行选中的模板函数
let result = await list[selectedKey].template(selectedText);
return result;
%>