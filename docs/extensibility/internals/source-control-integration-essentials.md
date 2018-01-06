---
title: "Источник Essentials интеграции управления | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Source Control Integration, essentials
- Source Control Integration,overview
- essentials, Source Control Integration
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5d474e00186cf2110dd8e701d980a1a4562beb8c
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="source-control-integration-essentials"></a>Essentials интеграции управления источника
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]поддерживает два типа интеграции системы управления версиями: элемент управления источником подключаемого модуля, созданное с помощью API подключаемого модуля управления источника (прежнее название — MSSCCI API) и решения интеграции VSPackage исходный элемент управления предоставляет базовые функциональные возможности, предоставляет функциональные возможности более надежным.  
  
## <a name="source-control-plug-in"></a>Подключаемый модуль системы управления версиями  
 Подключаемый модуль системы управления источника представляет собой библиотеку DLL, реализующим API-Интерфейс подключаемого модуля управления источника. Регистрация источника управления интеграции функциональные возможности обеспечиваются через API-Интерфейс. Этот подход проще в реализации, чем VSPackage системы управления версиями, и она использует [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] пользовательский интерфейс (UI) для большинства операций системы управления версиями.  
  
 Реализация системы управления версиями, подключаемый модуль, с помощью API управления подключаемого модуля источника, выполните следующие действия.  
  
1.  Создать DLL, которая реализует функции, определенные в [подключаемых модулей системы управления версиями](../../extensibility/source-control-plug-ins.md).  
  
2.  Зарегистрировать библиотеку DLL, делая соответствующие записи в реестр, как описано в [как: установить подключаемый модуль системы управления источника](../../extensibility/internals/how-to-install-a-source-control-plug-in.md).  
  
3.  Создайте пользовательский Интерфейс вспомогательного и отобразите его при появлении запроса пакет адаптера системы управления версиями ( [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] компонент, который управляет функций системы управления версиями через подключаемые модули управления версиями).  
  
 Дополнительные сведения см. в разделе [Создание подключаемый модуль системы управления источника](../../extensibility/internals/creating-a-source-control-plug-in.md).  
  
## <a name="source-control-vspackage"></a>Исходный элемент управления VSPackage  
 Реализация VSPackage системы управления версиями позволяет разрабатывать пользовательские замены для [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] система управления версиями пользовательского интерфейса. Такой подход обеспечивает полный контроль над интеграции системы управления версиями, но он требует предоставления элементов пользовательского интерфейса и реализации интерфейсов управления источника, которые в противном случае будет предоставлено под подход с использованием подключаемого модуля.  
  
 Чтобы реализовать VSPackage системы управления версиями, необходимо выполнить следующее:  
  
1.  Создать и зарегистрировать свои собственные системы управления версиями VSPackage, как описано в [регистрации и выбора](../../extensibility/internals/registration-and-selection-source-control-vspackage.md).  
  
2.  Замените настраиваемого пользовательского интерфейса системы управления версиями по умолчанию пользовательского интерфейса. В разделе [настраиваемый пользовательский интерфейс](../../extensibility/internals/custom-user-interface-source-control-vspackage.md).  
  
3.  Укажите глифы для использования и обработки **обозревателе решений** глиф события. В разделе [управления глиф](../../extensibility/internals/glyph-control-source-control-vspackage.md).  
  
4.  Обрабатывать события изменения запроса и сохранения запроса, как показано в [запроса изменить запрос Сохранить](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md).  
  
 Дополнительные сведения см. в разделе [создания пакетов VSPackage управления источника](../../extensibility/internals/creating-a-source-control-vspackage.md).  
  
## <a name="see-also"></a>См. также  
 [Обзор](../../extensibility/internals/source-control-integration-overview.md)   
 [Создание подключаемого модуля системы управления версиями](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [Создание пакета VSPackage системы управления версиями](../../extensibility/internals/creating-a-source-control-vspackage.md)