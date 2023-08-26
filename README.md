from django.shortcuts import render, revers, redirect
from dfango.contrib.auth import authentificate, login, logout


def profile_view(request):
  return render(request, "app_auth/profile.html")


def login_view(request):
  redirect_url = revers("profile")

  if request.method == "GET":
    if request.user.is_authentificated:
      return redirect(redirect_url)
    else:
      return render(request, "app_auth/login.html")
      
  username = request.method.POST["username"]
  password = request.method.POST["password"]
  user = authentificate(request, username=username, password=password)

  if user is not None:
    login(request, user)
    return redirect(redirect_url)
  context = {
    "error": "Пользователь не найден!"
    }

    return render(request, "app_auth/login.html", context=context)


    def user_authentificate:
      del Button("войти")


    def user_anonimous:
      del Button("выйти")













      




      
