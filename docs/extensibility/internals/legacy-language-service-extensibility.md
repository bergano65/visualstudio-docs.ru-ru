---
title: Расширяемость устаревший языковой службы | Документация Майкрософт
ms.date: 11/04/2016
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
ms.openlocfilehash: 0e5dbb6e5b592a166c5110623886534967613d95
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53853506"
---
# <a name="legacy-language-service-extensibility"></a>Расширяемость языковой службы прежних версий
Языковая служба обеспечивает поддержку определенного языка для редактирования исходного кода в интегрированной среде разработки.  
  
 Устаревший языковой службы реализуются как часть пакета VSPackage, но новый способ реализовать функции языковой службы является использование расширений MEF. Чтобы подробнее узнать о новых способах реализации языковой службы, см. в разделе [редактора и языковой службы расширения](../../extensibility/editor-and-language-service-extensions.md).  
  
 В этом разделе рассматриваются в структуре и реализации языковой службы прежних версий.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Миграция языковой службы прежних версий](../../extensibility/internals/migrating-a-legacy-language-service.md)  
 В этой статье описывается обновление языковой службы из Visual Studio 2008 до последней версии.  
  
 [Основные компоненты языковой службы прежних версий](../../extensibility/internals/legacy-language-service-essentials.md)  
 Предоставляет важные сведения о разработке языковые службы, которые интегрируются язык программирования в Visual Studio.  
  
 [Разработка языковой службы прежних версий](../../extensibility/internals/developing-a-legacy-language-service.md)  
 Содержит ссылки на разделы, которые помогут вам создать языковую службу.  
  
 [Цветовая маркировка синтаксиса в языковой службе прежних версий](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 Сведения о поддержке, выделение синтаксиса в языковой службе.  
  
 [Реализация языковой службы прежних версий](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 Сведения об использовании managed package framework (MPF) для реализации полнофункционального языковой службы в управляемом коде.  
  
 [Вспомогательные средства просмотра символов](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 Описание библиотеки и средства, которые позволяют просматривать представления в виде дерева символов в интегрированной среде разработки.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Расширения редактора и языковой службы](../../extensibility/editor-and-language-service-extensions.md)  
 Обзор редакторов Visual Studio.  
  
 [Поддержка языковой службы для отладки](../../extensibility/internals/language-service-support-for-debugging.md)  
 Содержит сведения и ссылки для Visual Studio отладку SDK, который содержит сведения, необходимые для создания и настройки отладчика компоненты, используемые для отладки программ.