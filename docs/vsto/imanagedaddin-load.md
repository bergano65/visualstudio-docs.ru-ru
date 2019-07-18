---
title: IManagedAddin::Load
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords: ''
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 87fb34e90d36383f49b6369fb1dea4b9854c7300
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62956735"
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
|*pdispApplication*|Указатель IDispatch, представляющий ведущее приложение, в которой загружается надстройка VSTO.|

## <a name="return-value"></a>Возвращаемое значение
 Значение HRESULT, указывающее, успешно ли завершен метод.

## <a name="remarks"></a>Примечания
 Манифест представляет собой файл (как правило, XML-файл), предоставляющий сведения, используемые для загрузки надстройки VSTO. Например, манифест может указывать расположение сборки надстройки VSTO и класс точки входа для создания экземпляра при загрузке надстройки VSTO.

 *BstrManifestURL* параметр содержит значение `Manifest` запись в разделе **HKEY_CURRENT_USER\Software\Microsoft\Office\\_\<имя приложения >_ \Addins\\_\<ИД надстройки >_**  раздел реестра для надстройки VSTO. Дополнительные сведения см. в разделе [интерфейс IManagedAddin](../vsto/imanagedaddin-interface.md).

 Реализуйте метод [IManagedAddIn::Load](../vsto/imanagedaddin-load.md) для выполнения таких задач, как настройка политики безопасности и домена приложения для загружаемой надстройки VSTO.

## <a name="see-also"></a>См. также
- [Интерфейс IManagedAddin](../vsto/imanagedaddin-interface.md)
- [IManagedAddin::Unload](../vsto/imanagedaddin-unload.md)
