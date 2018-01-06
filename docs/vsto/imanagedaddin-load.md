---
title: "IManagedAddin::Load | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: 
ms.assetid: 3faf9312-8ab4-4960-b2e7-8ca9859a3dcf
caps.latest.revision: "9"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 91a2909d407dbdc7629e189585333a3e4702483d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="imanagedaddinload"></a>IManagedAddin::Load
  Вызывается при загрузке управляемой надстройки VSTO.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT Load([in] BSTR bstrManifestURL,   
             [in] IDispatch *pdispApplication);  
```  
  
#### <a name="parameters"></a>Параметры  
  
|Параметр|Описание:|  
|---------------|-----------------|  
|*bstrManifestURL*|Полный путь манифеста для надстройки VSTO.|  
|*pdispApplication*|Указатель на IDispatch, представляющий ведущее приложение, загружающее надстройку VSTO.|  
  
## <a name="return-value"></a>Возвращаемое значение  
 Значение HRESULT, указывающее, успешно ли завершен метод.  
  
## <a name="remarks"></a>Примечания  
 Манифест представляет собой файл (как правило, XML-файл), предоставляющий сведения, используемые для загрузки надстройки VSTO. Например, манифест может указывать расположение сборки надстройки VSTO и класс точки входа для создания экземпляра при загрузке надстройки VSTO.  
  
 *BstrManifestURL* параметр содержит значение `Manifest` запись в HKEY_CURRENT_USER\Software\Microsoft\Office\\*\<имя приложения >*\Addins\\*\<ИД надстройки >* раздел реестра для надстройки VSTO. Для получения дополнительной информации см. [IManagedAddin Interface](../vsto/imanagedaddin-interface.md).  
  
 Реализуйте метод [IManagedAddIn::Load](../vsto/imanagedaddin-load.md) для выполнения таких задач, как настройка политики безопасности и домена приложения для загружаемой надстройки VSTO.  
  
## <a name="see-also"></a>См. также  
 [IManagedAddin Interface](../vsto/imanagedaddin-interface.md)   
 [IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)  
  
  