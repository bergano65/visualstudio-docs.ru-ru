---
title: IManagedAddin::Load
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
helpviewer_keywords: ''
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 605c1dc7a7b0d24ba082767930fd53148cccbd95
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920328"
---
# <a name="imanagedaddinload"></a>IManagedAddin::Load
  Вызывается при загрузке управляемой надстройки VSTO.

## <a name="syntax"></a>Синтаксис

```csharp
HRESULT Load([in] BSTR bstrManifestURL,
             [in] IDispatch *pdispApplication);
```

### <a name="parameters"></a>Параметры

|Параметр|Описание|
|---------------|-----------------|
|*bstrManifestURL*|Полный путь манифеста для надстройки VSTO.|
|*пдиспаппликатион*|Указатель на интерфейс IDispatch, представляющий ведущее приложение, которое загружает надстройку VSTO.|

## <a name="return-value"></a>Возвращаемое значение
 Значение HRESULT, указывающее, успешно ли завершен метод.

## <a name="remarks"></a>Remarks
 Манифест представляет собой файл (как правило, XML-файл), предоставляющий сведения, используемые для загрузки надстройки VSTO. Например, манифест может указывать расположение сборки надстройки VSTO и класс точки входа для создания экземпляра при загрузке надстройки VSTO.

 Параметр *бстрманифестурл* содержит значение `Manifest` записи в разделе реестра **HKEY_CURRENT_USER\Software\Microsoft\Office\\ _\<application name>_ \аддинс \\ _\<add-in ID>_** для надстройки VSTO. Дополнительные сведения см. в разделе [интерфейс IManagedAddin](../vsto/imanagedaddin-interface.md).

 Реализуйте метод [IManagedAddIn::Load](../vsto/imanagedaddin-load.md) для выполнения таких задач, как настройка политики безопасности и домена приложения для загружаемой надстройки VSTO.

## <a name="see-also"></a>См. также раздел
- [IManagedAddin - интерфейс](../vsto/imanagedaddin-interface.md)
- [IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)
