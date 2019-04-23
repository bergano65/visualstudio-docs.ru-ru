---
title: Практическое руководство. Доступ к встроенной шрифтов и цветовой схемы | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- fonts, accessing built-in
- font and color control [Visual Studio SDK], categories
- colors, accessing built-in schemes
ms.assetid: 6905845e-e88e-4805-adcf-21da39108ec7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 58d5fd0bfe1c8d5f5896d365a7b0ecfdb8da25b3
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60068227"
---
# <a name="how-to-access-the-built-in-fonts-and-color-ccheme"></a>Практическое руководство. Доступ к встроенной шрифты и цвета ccheme
В среде разработки Visual Studio (IDE) имеет схему шрифтов и цветов, связанный с окном редактора. Можно получить доступ к этой схемы через <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> интерфейс.

 Чтобы использовать встроенные шрифтов и цветов схемы, пакет VSPackage должен удовлетворять следующим требованиям:

- Определите категорию для использования со службой шрифты и цвета по умолчанию.

- Зарегистрируйте категории с сервером шрифты и цвета по умолчанию.

- Уведомления IDE, что с помощью отдельного окна использует встроенные отображаемые элементы и категории <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer> интерфейсов.

  Интегрированная среда разработки использует полученный категории как дескриптор окна. Имя категории будет отображаться в **Показать параметры для:** раскрывающегося списка в **шрифты и цвета** страницу свойств.

## <a name="to-define-a-category-using-built-in-fonts-and-colors"></a>Для определения категории с помощью встроенных шрифты и цвета

1. Создайте произвольный идентификатор GUID.

     Этот GUID используется для уникальной идентификации категорию. Повторно использует эту категорию, IDE по умолчанию шрифты и цвета спецификации.

    > [!NOTE]
    >  При получении данных шрифта и цвета с <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> или других интерфейсов, пакетов VSPackage использовать этот идентификатор GUID для ссылки на встроенные сведения.

2. Имя категории должны добавляться в таблицу строк внутри ресурсов в пакете VSPackage (*.rc*) файл, таким образом, чтобы можно было локализовать при необходимости при отображении в интегрированной среде разработки.

     Дополнительные сведения см. в разделе [Добавление или удаление строки](/cpp/windows/adding-or-deleting-a-string).

### <a name="to-register-a-category-using-built-in-fonts-and-colors"></a>Чтобы зарегистрировать категории, с помощью встроенных шрифты и цвета

1. Создайте специальный тип записи реестра категории в следующем расположении:

     *[HKLM\SOFTWARE\Microsoft \Visual Studio\\\<версия Visual Studio > \FontAndColors\\\<категории >*]

     *\<Категория >* нелокализованное имя категории.

2. Добавить в реестр для использования стандартных шрифтов и цветовой схемы с четырьмя значениями:

    |name|Тип|Данные|Описание|
    |----------|----------|----------|-----------------|
    |Категория|REG_SZ|Идентификатор GUID|Произвольный GUID, определяющий категорию, которая содержит акций шрифт и цветовую схему.|
    |Пакет|REG_SZ|Идентификатор GUID|{F5E7E71D-1401-11D1-883B-0000F87579D2}<br /><br /> Этот GUID используется всех пакетов VSPackage, использующих настройки шрифта и цвета по умолчанию.|
    |NameID|REG_DWORD|ID|Идентификатор ресурса имени категории локализуемых в VSPackage.|
    |ToolWindowPackage|REG_SZ|Идентификатор GUID|Идентификатор GUID VSPackage, реализующего <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> интерфейс.|

### <a name="to-initiate-the-use-of-system-provided-fonts-and-colors"></a>Для начала работы для системных шрифтов и цветов

1. Создайте экземпляр <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer> интерфейс как часть реализации и инициализации окна.

2. Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> метод, чтобы получить экземпляр <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer> интерфейс, соответствующий текущему <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> экземпляра.

3. Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> дважды.

   - Вызывать один раз с `VSEDITPROPID_ViewGeneral_ColorCategory`как аргумент.

   - Вызывать один раз с `VSEDITPROPID_ViewGeneral_FontCategory` как аргумент.

     Это задает и предоставляет службы шрифты и цвета по умолчанию как свойство окна.

## <a name="example"></a>Пример
 Следующий пример запускает использование встроенных шрифты и цвета.

```cpp
CComVariant vt;
CComQIPtr<IVsTextEditorPropertyCategoryContainer> spPropCatContainer(m_spView);
if (spPropCatContainer != NULL){
    CComPtr<IVsTextEditorPropertyContainer> spPropContainer;
    if (SUCCEEDED(spPropCatContainer->GetPropertyCategory(GUID_EditPropCategory_View_MasterSettings,
                                                          &spPropContainer))){
        CComVariant vt;CComVariant VariantGUID(bstrGuidText);
        spPropContainer->SetProperty(VSEDITPROPID_ViewGeneral_FontCategory, VariantGUID);
        spPropContainer->SetProperty(VSEDITPROPID_ViewGeneral_ColorCategory, VariantGUID);
    }
}
```

## <a name="see-also"></a>См. также

- [Использовать шрифты и цвета](../extensibility/using-fonts-and-colors.md)
- [Получить данные шрифта и цвета для цветовое выделение текста](../extensibility/getting-font-and-color-information-for-text-colorization.md)
- [Доступ хранимой параметры шрифта и цвета](../extensibility/accessing-stored-font-and-color-settings.md)
- [Общие сведения о шрифте и цвете](../extensibility/font-and-color-overview.md)