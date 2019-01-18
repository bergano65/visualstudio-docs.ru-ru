---
title: Интерфейс IDebugSessionProviderEx | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 26c5da2d-8c93-4d2b-94d2-97aaa377dcfe
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fae1cf673f47d3be586f83320b2d2c38c817e2cf
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349222"
---
# <a name="idebugsessionproviderex-interface"></a>Интерфейс IDebugSessionProviderEx
Основной интерфейс, предоставляемый с помощью отладчика интегрированной среды разработки для отладки узла и инициирован языка. Он устанавливает сеанс отладки для запущенного приложения. Этот интерфейс реализуется диспетчера отладки.  
  
 Помимо методов, наследуемых от `IUnknown`, `IDebugSessionProviderEx` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание:|  
|------------|-----------------|  
|[IDebugSessionProviderEx:CanJITDebug](../../winscript/reference/idebugsessionproviderex-canjitdebug.md)|Определяет, возможна ли отладка Just In Time с указанным приложением.|  
|[IDebugSessionProviderEx:StartDebugSession](../../winscript/reference/idebugsessionproviderex-startdebugsession.md)|Инициирует сеанс отладки с указанным приложением.|