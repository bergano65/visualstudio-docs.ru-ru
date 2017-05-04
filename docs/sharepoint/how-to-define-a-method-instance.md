---
title: "Практическое руководство. Определение экземпляра метода | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "подключение к бизнес-данным [разработка приложений SharePoint в Visual Studio], метод"
  - "подключение к бизнес-данным [разработка приложений SharePoint в Visual Studio], экземпляр метода"
  - "служба подключения к бизнес-данным [разработка приложений SharePoint в Visual Studio], метод"
  - "служба подключения к бизнес-данным [разработка приложений SharePoint в Visual Studio], экземпляр метода"
ms.assetid: f0c8a686-c0de-414e-8de9-f228f59d1eb3
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Практическое руководство. Определение экземпляра метода
  Необходимо определить хотя бы один экземпляр метода для каждого метода в модели.  
  
 Добавьте экземпляр метода в окне **Подробности метода BDC**.  При добавлении экземпляра метода Visual Studio добавляет элемент `<MethodInstance>` в XML\-код файла модели соответствующего проекта.  Дополнительные сведения об атрибутах элемента `<MethodInstance>` см. в разделе [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).  
  
### Определение экземпляра метода  
  
1.  В окне **Подробности метода BDC** последовательно разверните узел метода и узел **Экземпляры**.  
  
2.  В раскрывающемся списке **Добавить экземпляр метода** выберите **Создать экземпляр метода поиска**.  
  
     Под узлом **Экземпляры** отобразится новый экземпляр метода.  
  
3.  В строке меню последовательно выберите **Вид**, **Окно свойств**.  
  
4.  В окне **Свойства** задайте свойства экземпляра метода.  Дополнительные сведения о каждом свойстве см. в разделе [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).  
  
## См. также  
 [Общие сведения о средствах разработки моделей подключения к бизнес-данным](../sharepoint/bdc-model-design-tools-overview.md)   
 [Практическое руководство. Добавление сущности в модель](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Практическое руководство. Добавление параметра в метод](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Практическое руководство. Определение дескриптора типа параметра](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Проектирование модели подключения к бизнес-данным](../sharepoint/designing-a-business-data-connectivity-model.md)  
  
  