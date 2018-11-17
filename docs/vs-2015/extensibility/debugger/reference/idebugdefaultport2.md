---
title: IDebugDefaultPort2 | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugDefaultPort2
helpviewer_keywords:
- IDebugDefaultPort2 interface
ms.assetid: 7b3452af-9a96-4c4c-9946-4339b72d3d7b
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d9367968f08116a21ea51fc1d0167fa57a5e3bd7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51724488"
---
# <a name="idebugdefaultport2"></a>IDebugDefaultPort2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот интерфейс предоставляет несколько методов для работы порта сервера и средства уведомлений.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugDefaultPort2 : IDebugPort2  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Visual Studio реализует этот интерфейс для представления порта отладки для доступа к программам. Поставщика пользовательского порта также можно реализовать этот интерфейс, если производится обработка удаленной отладки.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 Аргумент методам [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) интерфейс поддерживает этот интерфейс. Вызов [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) на [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) интерфейс можно также получить этот интерфейс.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 Помимо методов, определенных в [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md), этот интерфейс реализует следующие методы:  
  
|Метод|Описание:|  
|------------|-----------------|  
|[GetPortNotify](../../../extensibility/debugger/reference/idebugdefaultport2-getportnotify.md)|Получает интерфейс уведомлений порт от данного порта.|  
|[GetServer](../../../extensibility/debugger/reference/idebugdefaultport2-getserver.md)|Получает интерфейс, сервер, содержащий этот порт.|  
|[QueryIsLocal](../../../extensibility/debugger/reference/idebugdefaultport2-queryislocal.md)|Определяет, выполняется ли этот порт на локальном компьютере.|  
  
## <a name="remarks"></a>Примечания  
 Имя "`IDebugDefaultPort2`» является немного неверно, так как он не представляет порт по умолчанию. Он может вызываться «IDebugPort3.»  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)

