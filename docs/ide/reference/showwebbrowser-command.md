---
title: "Команда ShowWebBrowser | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: view.showwebbrowser
helpviewer_keywords:
- ShowWebBrowser command
- View.ShowWebBrowser command
ms.assetid: c6a4fbd6-8e9d-45cc-8b2f-93990d065e78
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 122a5029c5518d7a4778c4d4732f7ebac9b23683
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="showwebbrowser-command"></a>Команда ShowWebBrowser
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