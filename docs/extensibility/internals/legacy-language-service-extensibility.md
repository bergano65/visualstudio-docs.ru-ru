---
title: "Расширяемость устаревших языковой службы | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "языковые службы"
  - "Visual Studio, языковые службы"
ms.assetid: 2700cd4d-5f68-43fc-b62f-dc80c3f3aa85
caps.latest.revision: 42
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 42
---
# Расширяемость устаревших языковой службы
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Языковая служба предоставляет языковой поддержки для редактирования исходного кода в Интегрированной среде разработки.  
  
 Устаревший языковые службы реализуются как частью VSPackage, но это использование расширений MEF новый способ реализации возможностей службы языка. Чтобы больше узнать о новый способ реализации службы языка, в разделе [Редактор и расширения службы языка](../../extensibility/editor-and-language-service-extensions.md).  
  
 В этом разделе описывает структуру и реализацию службы языка прежних версий.  
  
## В этом подразделе  
 [Миграция языковую службу для прежних версий](../../extensibility/internals/migrating-a-legacy-language-service.md)  
 Описание обновления языковую службу из Visual Studio 2008 до последней версии.  
  
 [Essentials устаревших языковой службы](../../extensibility/internals/legacy-language-service-essentials.md)  
 Важные сведения о разработке языковые службы интеграции языка программирования в Visual Studio.  
  
 [Разработка службы языка](../../extensibility/internals/developing-a-legacy-language-service.md)  
 Ссылки на разделы, которые помогут вам создать языковую службу.  
  
 [Синтаксиса в языковую службу для прежних версий](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 Сведения о поддержке, выделение синтаксиса в языковой службы.  
  
 [Реализация службы языка прежних версий](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 Сведения об использовании платформа управляемых пакетов \(MPF\) для реализации полнофункционального языковую службу в управляемом коде.  
  
 [Вспомогательные средства просмотра символов](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 Описание библиотеки и средства, позволяющие выбрать представления дерева символов в Интегрированной среде разработки.  
  
## Связанные подразделы  
 [Редактор и расширения службы языка](../../extensibility/editor-and-language-service-extensions.md)  
 Общие сведения о редакторах Visual Studio.  
  
 [Поддержка службы языка для отладки](../../extensibility/internals/language-service-support-for-debugging.md)  
 Содержит сведения и ссылки для Visual Studio отладка SDK, который содержит сведения, необходимые для создания и настройки компонентов отладчик для отладки программ.