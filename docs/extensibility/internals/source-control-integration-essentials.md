---
title: Источника Essentials Интеграция управления | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Source Control Integration, essentials
- Source Control Integration,overview
- essentials, Source Control Integration
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4533cac0ba6cbbcf5cf4354afdb29eefc5b2b726
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49879172"
---
# <a name="source-control-integration-essentials"></a>Основные элементы интеграции системы управления версиями
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] поддерживает два типа интеграция системы управления версиями: подключаемый модуль источника управления, который предоставляет базовые функциональные возможности и построен с использованием источника управления Plug-in API (прежнее название MSSCCI API) и интеграции решения управления исходный пакет VSPackage, предоставляет функциональные возможности более надежной.  
  
## <a name="source-control-plug-in"></a>Подключаемый модуль системы управления версиями  
 Подключаемый модуль системы управления источника записывается как библиотеку DLL, которая реализует API подключаемых модулей управления источника. Регистрация и источника управления интеграцией предоставляется через API. Этот подход проще в реализации, чем пакет VSPackage системы управления версиями, и он использует [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] пользовательский интерфейс (UI) для большинства операций управления версиями.  
  
 Реализация системы управления версиями, подключаемый модуль с помощью API подключаемого модуля управления источника, выполните следующие действия.  
  
1. Создать библиотеку DLL, который реализует функции, указанные в [подключаемых модулей системы управления версиями](../../extensibility/source-control-plug-ins.md).  
  
2. Регистрации библиотеки DLL, сделав соответствующие записи в реестр, как описано в разделе [как: установить подключаемый модуль системы управления источника](../../extensibility/internals/how-to-install-a-source-control-plug-in.md).  
  
3. Создать вспомогательный объект пользовательского интерфейса и отобразить ее при появлении запроса адаптера пакет системы управления версиями ( [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] компонент, который обрабатывает функции системы управления версиями через подключаемых модулей системы управления версиями).  
  
   Дополнительные сведения см. в разделе [Создание подключаемого модуля управления источника](../../extensibility/internals/creating-a-source-control-plug-in.md).  
  
## <a name="source-control-vspackage"></a>Пакет VSPackage управления версиями  
 Реализацию VSPackage системы управления версиями можно разрабатывать настраиваемый заменой [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] система управления версиями пользовательского интерфейса. Такой подход обеспечивает полный контроль над интеграция системы управления версиями, но он требует предоставления элементов пользовательского интерфейса и реализует интерфейсы управления источника, которые в противном случае будет передаваться в метод подключаемого модуля.  
  
 Для реализации пакета VSPackage системы управления версиями, необходимо сделать следующее:  
  
1. Создать и зарегистрировать свои собственные системы управления версиями VSPackage, как описано в разделе [регистрации и выбора](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).  
  
2. Замените настраиваемого пользовательского интерфейса системы управления версиями по умолчанию пользовательского интерфейса. См. в разделе [настраиваемый пользовательский интерфейс](../../extensibility/internals/custom-user-interface-source-control-vspackage.md).  
  
3. Укажите глифов для использования и обработки **обозревателе решений** события глифа. См. в разделе [элемент управления глифа](../../extensibility/internals/glyph-control-source-control-vspackage.md).  
  
4. Обрабатывать события изменения запросов и сохранения запроса, как показано в [запроса изменить запрос Сохранить](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md).  
  
   Дополнительные сведения см. в разделе [Создание пакета VSPackage управления версиями](../../extensibility/internals/creating-a-source-control-vspackage.md).  
  
## <a name="see-also"></a>См. также  
 [Обзор](../../extensibility/internals/source-control-integration-overview.md)   
 [Создание подключаемого модуля системы управления версиями](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [Создание пакета VSPackage системы управления версиями](../../extensibility/internals/creating-a-source-control-vspackage.md)