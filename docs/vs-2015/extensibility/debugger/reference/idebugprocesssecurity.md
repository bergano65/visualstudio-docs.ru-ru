---
title: IDebugProcessSecurity | Документация Майкрософт
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
- IDebugProcessSecurity interface
ms.assetid: 8a52ddca-bd99-49c0-9778-469dce7abd44
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5c3cfa0d8ef0f43b21ec2057b71b688b2d3ecb66
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47559800"
---
# <a name="idebugprocesssecurity"></a>IDebugProcessSecurity
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugProcessSecurity](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprocesssecurity).  
  
`IDebugProcessSecurity` реализуется, чтобы предупредить пользователя, что присоединение к процессу небезопасна поставщика порта.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugProcessSecurity : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugProcessSecurity`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetUserName](../../../extensibility/debugger/reference/idebugprocesssecurity-getusername.md)|Возвращает имя пользователя от поставщика порта.|  
|[QueryCanSafelyAttach](../../../extensibility/debugger/reference/idebugprocesssecurity-querycansafelyattach.md)|Предупреждает пользователя о небезопасна, присоединение к процессу отладки.|  
  
## <a name="remarks"></a>Примечания  
 Реализация этого интерфейса позволяет показать предупреждение и разрешить пользователю отменить, если процесс, к которому вы присоединяете может рассматриваться как небезопасные.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Порты](../../../extensibility/debugger/ports.md)   
 [Поставщики портов](../../../extensibility/debugger/port-suppliers.md)   
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)

