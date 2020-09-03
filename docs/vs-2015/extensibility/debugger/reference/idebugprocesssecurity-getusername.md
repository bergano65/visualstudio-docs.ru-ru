---
title: 'Идебугпроцесссекурити:: имя_пользователя | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 17a6ef52d7df1c60b0cb6581a7e15eeaf67e7875
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202785"
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает имя пользователя от поставщика порта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetUserName(  
    BSTR *pbstrUserName  
);  
```  
  
```csharp  
int GetUserName (  
    string pbstrUserName  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pbstrUserName`  
 заполняет Строка, содержащая имя пользователя.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Если метод завершается успешно, возвращает значение `S_OK`. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Remarks  
 `GetUserName` Возвращает имя пользователя, отображаемое в столбце **имя пользователя** диалогового окна **Присоединение к процессу** . Чтобы открыть диалоговое окно **Присоединение к процессу** , щелкните **присоединить к процессу** в меню **Сервис** в [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] интегрированной среде разработки (IDE).  
  
## <a name="see-also"></a>См. также:  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
