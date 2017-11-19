---
title: "IDebugProcessSecurity::GetUserName | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
caps.latest.revision: "4"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 909c4b4e47bdc9de60b9761974843b370c7400e1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
Возвращает имя пользователя из поставщика порта.  
  
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
 Если метод выполнен успешно, возвращается значение `S_OK`. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 `GetUserName`Возвращает имя пользователя, который отображается в **имя пользователя** столбец **присоединиться к процессу** диалоговое окно. Чтобы просмотреть **присоединиться к процессу** диалоговое окно, нажмите кнопку **присоединиться к процессу** на **средства** меню в [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки (IDE).  
  
## <a name="see-also"></a>См. также  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)