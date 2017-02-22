---
title: "Создание VSPackage управления источника | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Система управления версиями [Visual Studio SDK] Создание пакетов систем управления версиями"
  - "пакеты управления исходным кодом"
ms.assetid: cca0a9ed-48ff-409f-8036-ed8db0f7533e
caps.latest.revision: 23
caps.handback.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
---
# Создание VSPackage управления источника
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Эта документация содержит ссылки на обзору архитектуры интегрированного пакета для системы управления версиями [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]api\-интерфейс, которое определяется интерфейсами, который необходимо реализовать и службы, которую необходимо использовать, а также образец, иллюстрирующий простую реализацию пакета системы управления версиями.  
  
 С системой управления версиями VSPackage, можно создать глубокий путь integration services для системы управления версиями для интеграции с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Она позволяет пакету обойти по умолчанию размещается пользовательского интерфейса системы управления версиями by [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]в ответ на запросы системы управления версиями из системы проекта и взаимодействовать с  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] компоненты как  **Обозреватель решений**.  [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] уполномочивает  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] участники с механизмом для создания VSPackage, которые могут интегрировать с  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] использование модели службы.  
  
## В этом подразделе  
 [Начало работы](../../extensibility/internals/getting-started-with-source-control-vspackages.md)  
 Описание пакета системы управления версиями, более альтернативы дополнительно подключаемому модулю системы управления версиями для реализации функций системы управления версиями в пределах [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Архитектура](../../extensibility/internals/source-control-vspackage-architecture.md)  
 Представляет схему, а также компоненты пакета системы управления версиями.  
  
 [Функции](../../extensibility/internals/source-control-vspackage-features.md)  
 Описываются различные функции пакета системы управления версиями.  
  
 [Элементы макета](../../extensibility/internals/source-control-vspackage-design-elements.md)  
 Описывает структуру пакета VSPackage, системы управления версиями, должен реализовывать для глубокой интеграции.  
  
## Связанные подразделы  
 [Создание подключаемого модуля системы управления версиями](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 Описывает, как создать подключаемый модуль системы управления версиями эта функциональность предоставляет в системе управления версиями [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] пользовательский интерфейс системы управления версиями \(пользовательский интерфейс\).  
  
 [Система управления версиями](../../extensibility/internals/source-control.md)  
 Описывает параметры для реализации системы управления версиями, как интегрированная функция [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].