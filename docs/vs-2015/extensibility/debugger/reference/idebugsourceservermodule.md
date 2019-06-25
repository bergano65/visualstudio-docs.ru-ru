---
title: IDebugSourceServerModule | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugSourceServerModule interface
ms.assetid: 38213060-451d-46e6-8b4a-efc123e01a2c
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0dec9408d0cd1907a533a8cabe740832fe652398
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62555700"
---
# <a name="idebugsourceservermodule"></a>IDebugSourceServerModule
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Представляет сведения об исходном сервере, содержащийся в PDB-файл.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugSourceServerModule : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Этот интерфейс реализуется подсистемы отладчика и используемые пользовательским Интерфейсом отладчика.  
  
## <a name="methods"></a>Методы  
 В следующей таблице показаны методы `IDebugSourceServerModule`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetSourceServerData](../../../extensibility/debugger/reference/idebugsourceservermodule-getsourceserverdata.md)|Извлекает массив сведения об исходном сервере.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: Msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll
