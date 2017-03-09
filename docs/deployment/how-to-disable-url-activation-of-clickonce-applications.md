---
title: "Практическое руководство. Отключение активации по URL-адресу приложений ClickOnce | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "развертывание ClickOnce, активация URL-адреса"
  - "disallowUrlActivation"
  - "активация URL-адреса, приложения ClickOnce"
ms.assetid: db31a16b-960f-4264-91d7-c7c40f876068
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Практическое руководство. Отключение активации по URL-адресу приложений ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Как правило, приложение [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] запускается автоматически сразу после установки с веб\-сервера.  По соображениям безопасности можно отключить это поведение и сообщить пользователям, чтобы запускать приложение нужно из меню **Пуск**.  Следующая процедура описывает процесс отключения активации через URL.  
  
 Такой подход можно использовать только для приложений [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], установленных на компьютере пользователя с веб\-сервера.  Этот метод нельзя использовать для приложений, предназначенных только для использования в Интернете, запустить которые можно только с помощью URL.  Дополнительные сведения о различиях между приложениями для использования только в Интернете и установленными приложениями см. в разделе [Выбор стратегии развертывания ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 В этой процедуре используется инструмент в составе [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] MageUI.exe.  Дополнительные сведения об этом инструменте см. в разделе [MageUI.exe \(Manifest Generation and Editing Tool, Graphical Client\)](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md).  Кроме того, эту процедуру можно выполнить с помощью [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Процедура  
  
#### Отключение активации приложения с помощью URL  
  
1.  Откройте манифест развертывания в MageUI.exe.  Если вы еще не сделали этого, выполните шаги из документа [Разбор примера: развертывание вручную приложения ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
2.  Перейдите на вкладку **Параметры развертывания**.  
  
3.  Снимите флажок **Автоматически запускать приложение после установки**.  
  
4.  Сохраните и подпишите манифест.  
  
## См. также  
 [Публикация ClickOnce\-приложений](../deployment/publishing-clickonce-applications.md)