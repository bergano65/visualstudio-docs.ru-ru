---
title: Приступая к работе с подключаемых модулей системы управления версиями | Документация Майкрософт
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
- source control plug-ins, getting started
- getting started, source control plug-ins
ms.assetid: 46ac1f9f-4ecc-4a72-88d3-4c7e1647e1cb
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 56b38a1727d0ae859d12b1547e90705cdd6716e7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568739"
---
# <a name="getting-started-with-source-control-plug-ins"></a>Начало работы с подключаемыми модулями системы управления версиями
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Приступая к работе с подключаемых модулей системы управления версиями](https://docs.microsoft.com/visualstudio/extensibility/internals/getting-started-with-source-control-plug-ins).  
  
Создание подключаемого модуля системы управления версиями, необходимо создать библиотеку DLL, которая реализует функции, определенные в API подключаемых модулей управления источника, а затем зарегистрировать библиотеку DLL с [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] чтобы сделать его доступным для использования в системе управления версиями исходного кода.  
  
 Три версии API подключаемых модулей управления источника (версии 1.1, 1.2 и 1.3) доступны для подключаемых модулей системы управления версиями. API подключаемых модулей управления источника, здесь рассматриваются — версии 1.3. Она может быть полностью совместимы с подключаемых модулей системы управления версиями поддержка версий 1.1 и 1.2. [Новые возможности в версии 1.3 API подключаемого модуля источника управления](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md) разделе подробно описываются новые возможности, поддерживаемые в последней версии API подключаемых модулей управления источника.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Практическое руководство. Установка подключаемого модуля системы управления версиями](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)  
 В этой статье описывается создание записи в реестре, необходимые для подключаемого модуля системы управления версиями библиотеки DLL.  
  
 [Новые возможности в API версии 1.3 подключаемого модуля системы управления версиями](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)  
 Содержит краткий обзор изменений, внесенных в исходный API подключаемого модуля управления в версии 1.3.  
  
 [Новые возможности в API версии 1.2 подключаемого модуля системы управления версиями](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)  
 Содержит краткий обзор изменений, внесенных в исходный API подключаемого модуля управления в версии 1.2.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Подключаемые модули системы управления версиями](../../extensibility/source-control-plug-ins.md)  
 Предоставляет полный список всех элементов в API подключаемых модулей управления источника.  
  
 [Создание подключаемого модуля системы управления версиями](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 Определяет пакет SDK подключаемого модуля управления источника и описывает включаемые ресурсы.

