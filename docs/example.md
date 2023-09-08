#  用户输入指令“生成一个登录页面，用户需要输入用户名和密码进行登录”
role:
    user
content:
    Determine which agents use and respond using the format specified above.
    Task: <生成一个登录页面，用户需要输入用户名和密码进行登录>

# AI 的返回是一个 JSON，把任务下发给画布主管
role:
    assistant
content:
    {
        "thoughts": "首先，我们需要创建一个新的页面，然后在页面上添加用户名和密码的输入框以及登录按钮。",
        "command": {
            "name": "runAgent",
            "args": {
                "agentId": "canvas",
                "task": "创建新页面"
            }
        },
        "next": true
    }
