---
title: "Создание подключаемого модуля системы управления версиями | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- plug-ins, source control
- source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: c7e69fa4-150e-469a-a6fc-fa1260bdbb07
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e376ced68301abae6090a87114e2178c0adc28cf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="creating-a-source-control-plug-in"></a>Создание подключаемого модуля системы управления версиями
Пакет SDK для Visual Studio предоставляет ресурсы, которые позволяют добавлять возможности элемента управления источника для [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки (IDE). Он позволяет использовать любой подключаемый модуль библиотеки DLL, которая соответствует с API подключаемых модулей управления источника, описанные в этой документации.  
  
## <a name="in-this-section"></a>Содержание  
 [Начало работы](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)  
 Описывает, как установить подключаемый модуль системы управления версиями и выделяет в настоящее время доступных версий API подключаемых модулей для управления источника.  
  
 [Архитектура](../../extensibility/internals/source-control-plug-in-architecture.md)  
 Используется схема архитектуры объяснить интеграцию системы управления версиями, подключаемый модуль с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки.  
  
 [Руководство по тестированию подключаемых модулей системы управления версиями](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)  
 Руководство по проверке установки и функционирования подключаемый модуль системы управления версиями.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Создание пакета VSPackage системы управления версиями](../../extensibility/internals/creating-a-source-control-vspackage.md)  
 Описывает, как создать пакет VSPackage, который не только предоставляет функций системы управления версиями, но заменяет элемент управления источником [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] система управления версиями пользовательского интерфейса.  
  
 [Подключаемые модули системы управления версиями](../../extensibility/source-control-plug-ins.md)  
 Приводится полный список всех элементов API подключаемых модулей управления источника.  
  
 [Система управления версиями](../../extensibility/internals/source-control.md)  
 Описание параметров для реализации системы управления версиями в качестве интегрированной функцией [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].