---
title: 'IDebugProgramNode2:: Жетенгинеинфо | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetEngineInfo
helpviewer_keywords:
- IDebugProgramNode2::GetEngineInfo
ms.assetid: 664e7fe5-9100-4b7d-9dc5-e5a4dd0d0451
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1e3e24c2c326f7ebc7427da3804f17f1f75aeef4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205736"
---
# <a name="idebugprogramnode2getengineinfo"></a>IDebugProgramNode2::GetEngineInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает имя и идентификатор модуля отладки (DE), выполняющего программу.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetEngineInfo (   
   BSTR* pbstrEngine,  
   GUID* pguidEngine  
);  
```  
  
```csharp  
int GetEngineInfo(  
   out string pbstrEngine,   
   out Guid pguidEngine  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pbstrEngine`  
 заполняет Возвращает имя выключения программы (зависит от языка C++. это может быть пустой указатель, указывающий на то, что вызывающий объект не заинтересован в имени подсистемы).  
  
 `pguidEngine`  
 заполняет Возвращает глобальный уникальный идентификатор для отключения программы (относящийся к C++: это может быть пустой указатель, указывающий, что вызывающий объект не заинтересован в идентификаторе GUID подсистемы).  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также:  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
