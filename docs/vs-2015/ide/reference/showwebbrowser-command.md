---
title: Команда ShowWebBrowser | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- view.showwebbrowser
helpviewer_keywords:
- ShowWebBrowser command
- View.ShowWebBrowser command
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: de730650216f67d3f620fa85cad0a98148ce2ee3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47560487"
---
# <a name="showwebbrowser-command"></a>Команда ShowWebBrowser
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [команда ShowWebBrowser](https://docs.microsoft.com/visualstudio/ide/reference/showwebbrowser-command).  
  
  
Отображает URL-адрес, указанный в окне браузера внутри или вне интегрированной среды разработки (IDE).  
  
## <a name="syntax"></a>Синтаксис  
  
```  
View.ShowWebBrowser URL [/new][/ext]  
```  
  
## <a name="arguments"></a>Аргументы  
 `URL`  
 Обязательно. URL-адрес для веб-сайта.  
  
## <a name="switches"></a>Переключатели  
 /new  
 Необязательный. Указывает, что страница отображается в новом экземпляре браузера.  
  
 /ext  
 Необязательный. Указывает, что страница отображается в браузере по умолчанию вне интегрированной среды разработки.  
  
## <a name="remarks"></a>Примечания  
 Псевдоним для команды **ShowWebBrowser** имеет значение **navigate** или **nav**.  
  
## <a name="example"></a>Пример  
 Следующий пример отображает домашнюю страницу сайта MSDN в веб-браузере вне интегрированной среды разработки. Если экземпляр веб-браузера уже открыт, то используется он, в противном случае запускается новый экземпляр.  
  
```  
>View.ShowWebBrowser http://msdn.microsoft.com /ext  
```  
  
## <a name="see-also"></a>См. также  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Командное окно](../../ide/reference/command-window.md)   
 [Поле "Поиск/Команда"](../../ide/find-command-box.md)   
 [Псевдонимы команд Visual Studio](../../ide/reference/visual-studio-command-aliases.md)



