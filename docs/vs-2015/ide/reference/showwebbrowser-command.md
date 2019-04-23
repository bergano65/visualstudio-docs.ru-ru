---
title: Команда ShowWebBrowser | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- view.showwebbrowser
helpviewer_keywords:
- ShowWebBrowser command
- View.ShowWebBrowser command
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a1fc4f325167fa0df1f5f69cff19c25af5073d82
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59667902"
---
# <a name="showwebbrowser-command"></a>Команда ShowWebBrowser
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Отображает URL-адрес, указанный в окне браузера внутри или вне интегрированной среды разработки (IDE).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
View.ShowWebBrowser URL [/new][/ext]  
```  
  
## <a name="arguments"></a>Аргументы  
 `URL`  
 Обязательный. URL-адрес для веб-сайта.  
  
## <a name="switches"></a>Переключатели  
 /new  
 Необязательный параметр. Указывает, что страница отображается в новом экземпляре браузера.  
  
 /ext  
 Необязательный параметр. Указывает, что страница отображается в браузере по умолчанию вне интегрированной среды разработки.  
  
## <a name="remarks"></a>Примечания  
 Псевдоним для команды **ShowWebBrowser** имеет значение **navigate** или **nav**.  
  
## <a name="example"></a>Пример  
 Следующий пример отображает домашнюю страницу сайта MSDN в веб-браузере вне интегрированной среды разработки. Если экземпляр веб-браузера уже открыт, то используется он, в противном случае запускается новый экземпляр.  
  
```  
>View.ShowWebBrowser http://msdn.microsoft.com /ext  
```  
  
## <a name="see-also"></a>См. также раздел  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Командное окно](../../ide/reference/command-window.md)   
 [Поле "Поиск/Команда"](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
