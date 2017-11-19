---
title: "Создание элемента управления источника пакета VSPackage | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], creating source control packages
- source control packages
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
caps.latest.revision: "23"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4c3d414f1fcf6a7f4cd4155eb04e3696fb39740a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="creating-a-source-control-vspackage"></a>Создание элемента управления источника пакета VSPackage
Эта документация содержит ссылки на общие сведения об архитектуре системы управления версиями пакета интеграции с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], API, который определяется интерфейс для выполнения и служб для использования, а также пример, иллюстрирующий простой источника контролировать реализацию пакета.  
  
 С контролем исходного пакета VSPackage, можно создать глубокую интеграцию путь для системы управления версиями для интеграции с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Он позволяет пакету обхода системы управления версиями по умолчанию пользовательского интерфейса, поддерживаемого [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], отвечать на запросы системы управления версиями в системе проектов и взаимодействия с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] компонентов, таких как **обозревателе решений**. [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] Расширяет возможности [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] партнерам с механизм для создания пакетов VSPackage, который можно интегрировать с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] с помощью модели службы.  
  
## <a name="in-this-section"></a>Содержание  
 [Начало работы](../../extensibility/internals/getting-started-with-source-control-vspackages.md)  
 Описание источника пакета управления, который является более сложных альтернативой для реализации возможностей системы управления версиями в подключаемый модуль системы управления версиями [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Архитектура](../../extensibility/internals/source-control-vspackage-architecture.md)  
 Показана схема и приводится информация о компонентах пакета управления версиями.  
  
 [Функции](../../extensibility/internals/source-control-vspackage-features.md)  
 Описание различных функций пакета управления версиями.  
  
 [Элементы макета](../../extensibility/internals/source-control-vspackage-design-elements.md)  
 Описывает структуру VSPackage, который должен быть реализован пакет системы управления версиями для глубокой интеграции.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Создание подключаемого модуля системы управления версиями](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 Описывает, как создать элемент управления источником подключаемый модуль, предоставляющий функций системы управления версиями в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] исходного элемента управления пользовательского интерфейса (UI).  
  
 [Система управления версиями](../../extensibility/internals/source-control.md)  
 Описание параметров для реализации системы управления версиями в качестве интегрированной функцией [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].