---
title: Интерфейс IDebugSessionProvider | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugSessionProvider interface
ms.assetid: 1b898423-7af9-44f5-8dda-987005309c99
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d6d17546d5461a1ad76b144bf2652672ab4aa675
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345153"
---
# <a name="idebugsessionprovider-interface"></a>Интерфейс IDebugSessionProvider
Основной интерфейс, предоставленный с помощью отладчика интегрированной среды разработки для реализации узлов и языка инициировать отладки. Он устанавливает сеанс отладки для запущенного приложения. Этот интерфейс реализуется диспетчером отладки.  
  
 Помимо методов, наследуемых от `IUnknown`, `IDebugSessionProvider` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание:|  
|------------|-----------------|  
|[IDebugSessionProvider::StartDebugSession](../../winscript/reference/idebugsessionprovider-startdebugsession.md)|Инициирует сеанс отладки с указанным приложением.|