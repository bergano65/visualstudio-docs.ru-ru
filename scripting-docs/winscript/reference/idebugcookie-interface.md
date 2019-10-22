---
title: Интерфейс IDebugCookie | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugCookie interface
ms.assetid: 0dbc75d9-6f33-400f-a5bf-9122cf534082
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 47b48b917ee3376c417beffd9972d76a444513ef
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573192"
---
# <a name="idebugcookie-interface"></a>Интерфейс IDebugCookie
Позволяет задать куки-файл отладки для использования с интерфейсом `IMachineDebugManagerCookie`. Дополнительные сведения см. в разделе [интерфейс IMachineDebugManagerCookie](../../winscript/reference/imachinedebugmanagercookie-interface.md). Этот интерфейс реализуется диспетчером отладки процессов (PDM) и используется отладчиками скриптов.  
  
## <a name="methods"></a>Методы  
 В дополнение к методам, унаследованным от `IUnknown`, интерфейс `IDebugCookie` предоставляет следующие методы.  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDebugCookie::SetDebugCookie](../../winscript/reference/idebugcookie-setdebugcookie.md)|Задает файл cookie приложения отладки.|  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IMachineDebugManagerCookie](../../winscript/reference/imachinedebugmanagercookie-interface.md)