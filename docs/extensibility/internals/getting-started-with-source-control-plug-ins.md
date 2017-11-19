---
title: "Приступая к работе с подключаемые модули управления версиями | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, getting started
- getting started, source control plug-ins
ms.assetid: 46ac1f9f-4ecc-4a72-88d3-4c7e1647e1cb
caps.latest.revision: "21"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3ccbc7536a899226b7f2d9433b6c451df33bbde5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="getting-started-with-source-control-plug-ins"></a>Приступая к работе с подключаемые модули управления версиями
Чтобы создать подключаемый модуль системы управления версиями, необходимо создать библиотеку DLL, которая реализует функции, определенные в API подключаемых модулей управления источника, а затем зарегистрировать библиотеку DLL с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] чтобы сделать его доступным для использования в системе управления версиями исходного кода.  
  
 Три версии API подключаемых модулей управления источника (версии 1.1, 1.2 и 1.3) доступны для подключаемых модулей системы управления версиями. Здесь описаны API подключаемого модуля управления источника — версии 1.3. Она может быть полностью совместимы с подключаемые модули управления версиями поддержке версий 1.1 и 1.2. [Новые возможности источника управления Plug-in API версия 1.3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md) разделе описаны новые возможности, поддерживаемые в последней версии API-интерфейса подключаемого модуля управления источника.  
  
## <a name="in-this-section"></a>Содержание  
 [Практическое руководство. Установка подключаемого модуля системы управления версиями](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)  
 Описание способов сделать записи реестра, необходимые для подключаемого модуля системы управления версиями библиотеки DLL.  
  
 [Новые возможности в API версии 1.3 подключаемого модуля системы управления версиями](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)  
 Предоставляет общие сведения об изменениях, которые были внесены API подключаемых модулей управления источника в версии 1.3.  
  
 [Новые возможности в API версии 1.2 подключаемого модуля системы управления версиями](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)  
 Предоставляет общие сведения об изменениях, которые были внесены API подключаемых модулей управления источника в версии 1.2.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Подключаемые модули системы управления версиями](../../extensibility/source-control-plug-ins.md)  
 Приводится полный список всех элементов API подключаемых модулей управления источника.  
  
 [Создание подключаемого модуля системы управления версиями](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 Определяет SDK подключаемого модуля управления источника и описывает включены ресурсы.