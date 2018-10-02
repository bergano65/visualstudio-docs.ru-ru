---
title: Создание пакета VSPackage управления версиями | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], creating source control packages
- source control packages
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
caps.latest.revision: 24
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e67d21fe906dd6bc2a1da0a7a483ee78aa0fe2db
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562067"
---
# <a name="creating-a-source-control-vspackage"></a>Создание пакета VSPackage системы управления версиями
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Создание пакета VSPackage управления версиями](https://docs.microsoft.com/visualstudio/extensibility/internals/creating-a-source-control-vspackage).  
  
Эта документация содержит ссылки на обзор архитектуры пакета системы управления версиями интегрируется с [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], API, который определяется интерфейс для выполнения и служб для использования и пример, иллюстрирующий простой источника пакет реализацию элементов управления.  
  
 С помощью системы управления версиями VSPackage, можно создать путь глубокая интеграция системы управления версиями для интеграции с [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Он позволяет обойти системы управления версиями по умолчанию пользовательского интерфейса, поддерживаемого пакета [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], отвечать на запросы системы управления версиями в системе проектов и взаимодействовать с [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] компоненты, такие как **обозревателе решений**. [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] Расширяет возможности [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] сотрудничает с механизм для создания VSPackage, который можно интегрировать с [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] с помощью модели службы.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Начало работы](../../extensibility/internals/getting-started-with-source-control-vspackages.md)  
 Обсуждаются пакет системы управления версиями, который является альтернативой более сложные системы управления версиями, подключаемый модуль для реализации функций системы управления версиями в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
 [Архитектура](../../extensibility/internals/source-control-vspackage-architecture.md)  
 Представляет схему и приводится информация о компонентах пакета системы управления версиями.  
  
 [Функции](../../extensibility/internals/source-control-vspackage-features.md)  
 Описание различных возможностей пакета системы управления версиями.  
  
 [Элементы проектирования](../../extensibility/internals/source-control-vspackage-design-elements.md)  
 Описывает структуру пакета VSPackage, который должен быть реализован пакет системы управления версиями для глубокой интеграции.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Создание подключаемого модуля системы управления версиями](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 Создание системы управления версиями подключаемого модуля, предоставляющий функции системы управления версиями в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] интерфейс пользователя системы управления версиями (UI).  
  
 [Система управления версиями](../../extensibility/internals/source-control.md)  
 Обсуждаются параметры для реализации системы управления версиями в виде интегрированной функцией [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].

