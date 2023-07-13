# Review
import openai
import requests
import pyperclip  # 导入用于复制文本的库
import webbrowser  # 导入用于打开浏览器的库

# 设置OpenAI API密钥
openai.api_key = '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'

# 定义函数，用于生成评价文章
def generate_review(instruction):
    # 构建API请求的数据结构
    data = {
        'model': 'Forest House SPA',
        'prompt': instruction,
        'max_tokens': 200,
        'temperature': 0.6,
        'n': 1
    }

    # 调用OpenAI API，发送指示数据并接收响应
    response = openai.Completion.create(data=data)

    # 处理API的响应，提取生成的评价文章
    review = response.choices[0].text.strip()

    return review

# 示例指示
instruction = "Please help me write a review about this restaurant highlighting their delicious food and great service."

# 生成评价文章
review = generate_review(instruction)

# 打印生成的评价文章
print(review)

# 复制生成的评价文章到剪贴板
pyperclip.copy(review)

# 打开Google商家评价页面并粘贴评价
google_url = 'https://g.page/r/CehiwUdbQoJkEBM/review'
webbrowser.open(google_url)

# 提示用户手动粘贴评价到Google评价页面
