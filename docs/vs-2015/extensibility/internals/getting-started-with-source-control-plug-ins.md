---
title: начало работы с подключаемыми модулями системы управления версиями | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, getting started
- getting started, source control plug-ins
ms.assetid: 46ac1f9f-4ecc-4a72-88d3-4c7e1647e1cb
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 85aa5727f252ad75c45064d7b885e3d282da36a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538165"
---
# <a name="getting-started-with-source-control-plug-ins"></a>Начало работы с подключаемыми модулями системы управления версиями
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Чтобы создать подключаемый модуль системы управления версиями, необходимо создать библиотеку DLL, которая реализует функции, определенные в интерфейсе API подключаемого модуля системы управления версиями, а затем зарегистрировать библиотеку DLL с [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] целью сделать ее доступной для использования в системе управления версиями исходного кода.  
  
 Для подключаемых модулей системы управления версиями доступны три версии API подключаемого модуля системы управления версиями (версии 1,1, 1,2 и 1,3). API подключаемого модуля системы управления версиями, описанный здесь, — версия 1,3. Он был разработан для полной совместимости с подключаемыми модулями системы управления версиями, поддерживающими версии 1,1 и 1,2. В разделе новые возможности [API подключаемого модуля системы управления версиями 1,3](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md) описаны новые функции, поддерживаемые в последней версии API подключаемого модуля системы управления версиями.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Практическое руководство. Установка подключаемого модуля системы управления версиями](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)  
 Описывает, как создать записи реестра, необходимые для подключения к библиотеке DLL системы управления версиями.  
  
 [Новые возможности в API версии 1.3 подключаемого модуля системы управления версиями](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-3.md)  
 Содержит краткий обзор изменений, внесенных в API подключаемого модуля системы управления версиями в версии 1,3.  
  
 [Новые возможности в API версии 1.2 подключаемого модуля системы управления версиями](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)  
 Содержит краткий обзор изменений, внесенных в API подключаемого модуля системы управления версиями в версии 1,2.  
  
## <a name="related-sections"></a>См. также  
 [Подключаемые модули системы управления версиями](../../extensibility/source-control-plug-ins.md)  
 Содержит полный список всех элементов в интерфейсе API подключаемого модуля системы управления версиями.  
  
 [Создание подключаемого модуля системы управления версиями](../../extensibility/internals/creating-a-source-control-plug-in.md)  
 Определяет пакет SDK для подключаемого модуля системы управления версиями и описывает входящие ресурсы.
