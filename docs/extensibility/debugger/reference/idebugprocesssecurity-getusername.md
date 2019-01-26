---
title: IDebugProcessSecurity::GetUserName | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0922dc458bb836fd579dd4281be4cfbaf9b522f3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54958099"
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
Возвращает имя пользователя от поставщика порта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
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
 [out] Строка, содержащая имя пользователя.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Если метод завершается успешно, возвращается `S_OK`. В противном случае он возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 `GetUserName` Возвращает имя пользователя, который отображается в **имя пользователя** столбец **присоединение к процессу** диалоговое окно. Чтобы просмотреть **присоединение к процессу** диалоговом окне щелкните **присоединение к процессу** на **средства** меню в [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки (IDE).  
  
## <a name="see-also"></a>См. также  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)