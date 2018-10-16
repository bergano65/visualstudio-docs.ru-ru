---
title: Приступая к работе с подключаемых модулей системы управления версиями | Документация Майкрософт
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
ms.openlocfilehash: 2f1eb4f76616f6a5f6791cbcd1b8a5770d1dcabb
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2018
ms.locfileid: "39498104"
---
# <a name="get-started-with-source-control-plug-ins"></a>Начало работы с подключаемых модулей системы управления версиями
Создание подключаемого модуля системы управления версиями, необходимо создать библиотеку DLL, которая реализует функции, определенные в API подключаемых модулей управления источника, а затем зарегистрировать библиотеку DLL с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] чтобы сделать его доступным для использования в системе управления версиями исходного кода.  
  
 Три версии API подключаемых модулей управления источника (версии 1.1, 1.2 и 1.3) доступны для подключаемых модулей системы управления версиями. API подключаемых модулей управления источника, здесь рассматриваются — версии 1.3. Она может быть полностью совместимы с подключаемых модулей системы управления версиями поддержка версий 1.1 и 1.2. [Новые возможности в версии 1.3 API подключаемого модуля источника управления](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md) разделе подробно описываются новые возможности, поддерживаемые в последней версии API подключаемых модулей управления источника.  
  
## <a name="in-this-section"></a>Содержание раздела  
 [Как: установить подключаемый модуль системы управления версиями](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)  
 В этой статье описывается создание записи в реестре, необходимые для подключаемого модуля системы управления версиями библиотеки DLL.  
  
 [Новые возможности в версии 1.3 API подключаемого модуля источника элемента управления](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)  
 Содержит краткий обзор изменений, внесенных в исходный API подключаемого модуля управления в версии 1.3.  
  
 [Новые возможности в исходный элемент управления Plug-in API версии 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)  
 Содержит краткий обзор изменений, внесенных в исходный API подключаемого модуля управления в версии 1.2.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Подключаемых модулей системы управления версиями](../../extensibility/source-control-plug-ins.md)  
 Предоставляет полный список всех элементов в API подключаемых модулей управления источника.  
  
 [Создание подключаемого модуля системы управления версиями](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 Определяет пакет SDK подключаемого модуля управления источника и описывает включаемые ресурсы.