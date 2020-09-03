---
title: Создание пакета VSPackage для системы управления версиями | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], creating source control packages
- source control packages
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2b1516cf358a4488ff02e650f6c703a1761a94a2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196951"
---
# <a name="creating-a-source-control-vspackage"></a>Создание пакета VSPackage системы управления версиями
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Эта документация содержит ссылки на обзор архитектуры пакета управления версиями, интегрированного с [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , API, который определяется реализуемыми интерфейсами и используемыми службами, а также пример, иллюстрирующий простую реализацию пакета управления версиями.  
  
 С помощью пакета VSPackage системы управления версиями можно создать путь к глубокой интеграции для системы управления версиями, с которой будет осуществляться интеграция [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Он позволяет пакету обходить пользовательский интерфейс системы управления версиями по умолчанию [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , отвечающий на запросы к системе управления версиями, и взаимодействовать с [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] такими компонентами, как **Обозреватель решений**. Предоставляет [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] партнерам механизм создания пакета VSPackage, который может интегрироваться с [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] моделью службы.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Начало работы](../../extensibility/internals/getting-started-with-source-control-vspackages.md)  
 Описывает пакет управления версиями, который является более сложной альтернативой подключаемому модулю системы управления версиями для реализации функций системы управления версиями в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 [Архитектура](../../extensibility/internals/source-control-vspackage-architecture.md)  
 Представлена схема и объясняются компоненты пакета системы управления версиями.  
  
 [Функции](../../extensibility/internals/source-control-vspackage-features.md)  
 Описывает различные функции пакета системы управления версиями.  
  
 [Элементы проектирования](../../extensibility/internals/source-control-vspackage-design-elements.md)  
 Описывает структуру VSPackage, которую должен реализовать пакет системы управления версиями для глубокой интеграции.  
  
## <a name="related-sections"></a>См. также  
 [Создание подключаемого модуля системы управления версиями](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 Описывает создание подключаемого модуля системы управления версиями, предоставляющего функции управления версиями в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] пользовательском интерфейсе системы управления версиями.  
  
 [Система управления версиями](../../extensibility/internals/source-control.md)  
 Описывает варианты реализации системы управления версиями в качестве интегрированной функции [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .
