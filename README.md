# resume
import markdown
from weasyprint import HTML

# --- 第一部分：简历内容 (Markdown 格式) ---
# 这里已经根据你的联合国实习经历和教育背景进行了预填 [cite: 9, 20, 21]
resume_markdown = """
# Tongyu Wu (Lareina)
[Lareinawu111@gmail.com](mailto:Lareinawu111@gmail.com) | (+1) 551-359-0079
[Linkedin.com/in/tongyu-lareina-wu-530089290](https://Linkedin.com/in/tongyu-lareina-wu-530089290)

## PROFESSIONAL SUMMARY
Bilingual communication professional with international experience across US and APAC region. Skilled in corporate communications, brand storytelling, and multimedia production[cite: 4, 5, 6].

## WORK EXPERIENCE
**Public Information Intern** | The United Nations Headquarter, New York
*Nov 2025 – May 2026*
* Produce videos, graphic designs and digital communication materials aligned with institutional branding[cite: 22].
* Support communication activities for major events and high-level meetings, including on-site coordination[cite: 23].

**Communication Intern** | People's Daily English Edition, Beijing
*Jul 2025 – Oct 2025*
* Delivered cross-platform content (X, YouTube, TikTok) to boost brand visibility[cite: 28].
* Managed 10+ multimedia pieces from scriptwriting to final editing[cite: 29].

## EDUCATION
**The University of Melbourne** | Master of International Journalism [cite: 9]
**Beijing Sports University** | Bachelor of Data Science and Big Data Technology [cite: 14, 15]

## SKILLS
* **Languages:** English (Fluent), Mandarin (Native) [cite: 41]
* **Tools:** Adobe Premiere Pro, Photoshop, Canva, Python, C++ [cite: 16, 42]
"""

# --- 第二部分：视觉样式 (CSS 样式) ---
# 模仿你喜欢的“极简、留白、细线”风格
resume_css = """
@page { size: A4; margin: 2cm; }
body { 
    font-family: 'Helvetica', 'Arial', sans-serif; 
    line-height: 1.6; 
    color: #333; 
    margin: 0;
}
h1 { 
    font-size: 28pt; 
    font-weight: 300; 
    text-transform: uppercase; 
    letter-spacing: 5px; 
    border-bottom: 1px solid #000; 
    margin-bottom: 20px; 
}
h2 { 
    font-size: 12pt; 
    color: #666; 
    text-transform: uppercase; 
    letter-spacing: 2px; 
    margin-top: 25px; 
    border-left: 3px solid #000; 
    padding-left: 10px; 
}
p, li { font-size: 10pt; margin-bottom: 5px; }
strong { color: #000; }
a { color: #333; text-decoration: none; border-bottom: 1px aria-hidden="true" solid #ccc; }
"""

# --- 第三部分：转换逻辑 ---
def create_pdf():
    # 1. 将 Markdown 转换为 HTML
    html_body = markdown.markdown(resume_markdown)
    
    # 2. 拼接完整的 HTML 结构
    full_html = f"""
    <html>
    <head><style>{resume_css}</style></head>
    <body>{html_body}</body>
    </html>
    """
    
    # 3. 使用 WeasyPrint 生成 PDF
    HTML(string=full_html).write_pdf("Lareina_Resume_2026.pdf")
    print("✨ 简历生成成功！请检查当前文件夹下的 Lareina_Resume_2026.pdf")

if __name__ == "__main__":
    create_pdf()
