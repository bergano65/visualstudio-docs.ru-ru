---
title: Расширяемость устаревших языковой службы | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services
- Visual Studio, language services
ms.assetid: 2700cd4d-5f68-43fc-b62f-dc80c3f3aa85
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bb7d8165060fa3b9a6445ad71a977c79414056f3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="legacy-language-service-extensibility"></a>Расширяемость устаревших языковой службы
Языковая служба обеспечивает поддержку языка для редактирования исходного кода в Интегрированной среде разработки.  
  
 Прежних версий языка службы реализованы как часть пакета VSPackage, но новой реализации возможностей службы языка можно выполнить с помощью расширений MEF. Чтобы больше узнать о новых способ реализации языковую службу, в разделе [редактора и расширения службы языка](../../extensibility/editor-and-language-service-extensions.md).  
  
 В этом разделе рассматриваются структуру и реализацию службы языка прежних версий.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Миграция языковой службы прежних версий](../../extensibility/internals/migrating-a-legacy-language-service.md)  
 Объясняет, как обновить языковой службы из Visual Studio 2008 до последней версии.  
  
 [Основные компоненты языковой службы прежних версий](../../extensibility/internals/legacy-language-service-essentials.md)  
 Предоставляет важные сведения о разработке языковые службы интеграции на языке программирования в Visual Studio.  
  
 [Разработка языковой службы прежних версий](../../extensibility/internals/developing-a-legacy-language-service.md)  
 Ссылки на разделы, которые могут помочь в создании языковой службы.  
  
 [Цветовая маркировка синтаксиса в языковой службе прежних версий](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 Сведения о поддержке, выделение синтаксиса в службе языка.  
  
 [Реализация службы языка для прежних версий](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 Сведения об использовании платформы управляемых пакетов (MPF) для реализации службы полнофункциональный язык в управляемом коде.  
  
 [Вспомогательные средства просмотра символов](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 Описание библиотеки и средства, которые позволяют просматривать представления в виде дерева символов в Интегрированной среде разработки.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Расширения редактора и языковой службы](../../extensibility/editor-and-language-service-extensions.md)  
 Общие сведения о редакторах Visual Studio.  
  
 [Поддержка языковой службы для отладки](../../extensibility/internals/language-service-support-for-debugging.md)  
 Содержит сведения и ссылки для Visual Studio отладка пакета SDK, который содержит сведения, необходимые для создания и настройки компонентов отладчик, используемый для отладки программы.