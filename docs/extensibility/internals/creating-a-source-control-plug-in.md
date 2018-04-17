---
title: Создание подключаемого модуля системы управления версиями | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 04c6125004aaf2740b54acdce91bef032647c6e5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="creating-a-source-control-plug-in"></a>Создание подключаемого модуля системы управления версиями
Пакет SDK для Visual Studio предоставляет ресурсы, которые позволяют добавлять возможности элемента управления источника для [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки (IDE). Он позволяет использовать любой подключаемый модуль библиотеки DLL, которая соответствует с API подключаемых модулей управления источника, описанные в этой документации.  
  
## <a name="in-this-section"></a>В этом разделе  
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