---
title: Приступая к работе с подключаемые модули управления версиями | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, getting started
- getting started, source control plug-ins
ms.assetid: 46ac1f9f-4ecc-4a72-88d3-4c7e1647e1cb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3f5c88d932fd2915273c86924d2df8f1233baeed
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128924"
---
# <a name="getting-started-with-source-control-plug-ins"></a>Приступая к работе с подключаемые модули управления версиями
Чтобы создать подключаемый модуль системы управления версиями, необходимо создать библиотеку DLL, которая реализует функции, определенные в API подключаемых модулей управления источника, а затем зарегистрировать библиотеку DLL с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] чтобы сделать его доступным для использования в системе управления версиями исходного кода.  
  
 Три версии API подключаемых модулей управления источника (версии 1.1, 1.2 и 1.3) доступны для подключаемых модулей системы управления версиями. Здесь описаны API подключаемого модуля управления источника — версии 1.3. Она может быть полностью совместимы с подключаемые модули управления версиями поддержке версий 1.1 и 1.2. [Новые возможности источника управления Plug-in API версия 1.3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md) разделе описаны новые возможности, поддерживаемые в последней версии API-интерфейса подключаемого модуля управления источника.  
  
## <a name="in-this-section"></a>В этом разделе  
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