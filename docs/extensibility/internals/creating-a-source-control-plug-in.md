---
title: Создание подключаемого модуля системы управления версиями | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: c7e69fa4-150e-469a-a6fc-fa1260bdbb07
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f8b6578923134d1aaaeb2c60eb118ab66e71d27e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53888092"
---
# <a name="create-a-source-control-plug-in"></a>Создание подключаемого модуля системы управления версиями
Пакет SDK для Visual Studio предоставляет ресурсы, которые позволяют добавлять возможности элемента управления источника для [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки (IDE). Он позволяет использовать библиотеку DLL для подключаемого модуля, который соответствует с API подключаемых модулей управления источника, приведенные в этой документации.  
  
## <a name="in-this-section"></a>Содержание раздела  
 [Начало работы](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)  
 Описывается, как установить подключаемый модуль системы управления версиями и выделяет в настоящее время доступные версии API подключаемого модуля управления источника.  
  
 [Архитектура](../../extensibility/internals/source-control-plug-in-architecture.md)  
 Использует схему архитектуры, чтобы объяснить, интеграция системы управления версиями, подключаемый модуль с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки.  
  
 [Руководство по тестирования](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)  
 Содержит рекомендации о том, как для проверки установки и работы подключаемого модуля системы управления версиями.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Создать пакет VSPackage системы управления версиями](../../extensibility/internals/creating-a-source-control-vspackage.md)  
 Описывает, как создать пакет VSPackage, который не только предоставляет функции системы управления версиями, но заменяет элемент управления источником [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] система управления версиями пользовательского интерфейса.  
  
 [Подключаемых модулей системы управления версиями](../../extensibility/source-control-plug-ins.md)  
 Предоставляет полный список всех элементов в API подключаемых модулей управления источника.  
  
 [Системы управления версиями](../../extensibility/internals/source-control.md)  
 Обсуждаются параметры для реализации системы управления версиями в виде интегрированной функцией [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].
