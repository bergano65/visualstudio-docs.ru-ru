---
title: Создание пакета VSPackage управления версиями | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], creating source control packages
- source control packages
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0d9513410aa3bb4773629846abbd70159ec6aa77
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2018
ms.locfileid: "39499742"
---
# <a name="create-a-source-control-vspackage"></a>Создать пакет VSPackage системы управления версиями
Эта документация содержит ссылки на обзор архитектуры пакета системы управления версиями интегрируется с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], API, который определяется интерфейс для выполнения и служб для использования и пример, иллюстрирующий простой источника пакет реализацию элементов управления.  
  
 С помощью системы управления версиями VSPackage, можно создать путь глубокая интеграция системы управления версиями для интеграции с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Он позволяет обойти системы управления версиями по умолчанию пользовательского интерфейса, поддерживаемого пакета [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], отвечать на запросы системы управления версиями в системе проектов и взаимодействовать с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] компоненты, такие как **обозревателе решений**. [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Расширяет возможности [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] сотрудничает с механизм для создания VSPackage, который можно интегрировать с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] с помощью модели службы.  
  
## <a name="in-this-section"></a>Содержание раздела  
 [Начало работы](../../extensibility/internals/getting-started-with-source-control-vspackages.md)  
 Обсуждаются пакет системы управления версиями, который является альтернативой более сложные системы управления версиями, подключаемый модуль для реализации функций системы управления версиями в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Архитектура](../../extensibility/internals/source-control-vspackage-architecture.md)  
 Представляет схему и приводится информация о компонентах пакета системы управления версиями.  
  
 [Функции](../../extensibility/internals/source-control-vspackage-features.md)  
 Описание различных возможностей пакета системы управления версиями.  
  
 [Элементы проектирования](../../extensibility/internals/source-control-vspackage-design-elements.md)  
 Описывает структуру пакета VSPackage, который должен быть реализован пакет системы управления версиями для глубокой интеграции.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Создание подключаемого модуля системы управления версиями](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 Создание системы управления версиями подключаемого модуля, предоставляющий функции системы управления версиями в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интерфейс пользователя системы управления версиями (UI).  
  
 [Системы управления версиями](../../extensibility/internals/source-control.md)  
 Обсуждаются параметры для реализации системы управления версиями в виде интегрированной функцией [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].
