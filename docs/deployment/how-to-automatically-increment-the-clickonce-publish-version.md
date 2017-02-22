---
title: "Практическое руководство. Автоматическое увеличение номера версии публикации ClickOnce | Microsoft Docs"
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
  - "развертывание ClickOnce, автоматическое увеличение версии публикации"
  - "развертывание приложений [ClickOnce], автоматическое увеличение версии публикации"
  - "Версия публикации - свойство, увеличение"
  - "публикация, ClickOnce"
ms.assetid: 686ab88a-6305-4914-a05b-fe269cc0ae1e
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Практическое руководство. Автоматическое увеличение номера версии публикации ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

При публикации приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] изменение свойства `Publish Version` вызывает публикацию приложения как обновление.  По умолчанию Visual Studio автоматически увеличивает номер `Revision` версии `Publish Version` при каждой публикации приложения.  
  
 Это поведение можно отключить на странице **Публикация** в **конструкторе проектов**.  
  
> [!NOTE]
>  Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих настроек или выпуска.  Чтобы изменить параметры, в меню **Сервис** выберите команду **Импорт и экспорт параметров**.  Дополнительные сведения см. в разделе [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ru-ru/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Автоматическое отключение увеличения номера версии публикации  
  
1.  Выбрав проект в **обозревателе решений**, в меню **Проект** выберите пункт **Свойства**.  
  
2.  Выберите вкладку **Публикация**.  
  
3.  В разделе **Версия публикации** сбросьте флажок **Автоматическое внесение изменений при каждом выпуске**.  
  
## См. также  
 [Практическое руководство. Установка версии публикации приложения ClickOnce](../Topic/How%20to:%20Set%20the%20ClickOnce%20Publish%20Version.md)   
 [Публикация ClickOnce\-приложений](../deployment/publishing-clickonce-applications.md)   
 [Практическое руководство. Публикация приложения ClickOnce с помощью мастера публикации](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)