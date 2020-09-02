---
title: Пошаговое руководство. доступ к встроенным шрифтам и цветовой схеме | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, accessing built-in
- font and color control [Visual Studio SDK], categories
- colors, accessing built-in schemes
ms.assetid: 6905845e-e88e-4805-adcf-21da39108ec7
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a43fb3a22ecb2d04542eacf07bf883590868b75b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685306"
---
# <a name="how-to-access-the-built-in-fonts-and-color-scheme"></a>Практическое руководство. Доступ к встроенным шрифтам и цветовой схеме
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Интегрированная среда разработки (IDE) Visual Studio имеет схему шрифтов и цветов, связанных с окном редактора. Доступ к этой схеме можно получить через <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> интерфейс.  
  
 Для использования встроенной схемы шрифтов и цветов пакет VSPackage должен:  
  
- Определите категорию для использования со службой шрифтов и цветов по умолчанию.  
  
- Зарегистрируйте категорию на сервере шрифтов и цветов по умолчанию.  
  
- Рекомендовать интегрированной среде разработки, что определенное окно использует встроенные отображаемые элементы и категории, с `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` помощью `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` интерфейсов и.  
  
  В интегрированной среде разработки в качестве маркера окна используется результирующая категория. Имя категории отображается в раскрывающемся списке **Показать параметры для:** на странице свойств **шрифты и цвета** .  
  
### <a name="to-define-a-category-using-built-in-fonts-and-colors"></a>Определение категории с помощью встроенных шрифтов и цветов  
  
1. Создайте произвольный идентификатор GUID.  
  
    Этот идентификатор GUID используется для уникальной идентификации категории<strong>.</strong> Эта категория повторно использует спецификацию шрифтов и цветов IDE по умолчанию.  
  
   > [!NOTE]
   > При извлечении данных шрифтов и цветов с помощью <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> или других интерфейсов пакеты VSPackage используют этот GUID для ссылки на встроенные сведения.  
  
2. Имя категории должно быть добавлено в таблицу строк в файле ресурсов VSPackage (. RC), чтобы его можно было локализовать при отображении в интегрированной среде разработки.  
  
    Дополнительные сведения см. [в разделе Добавление или удаление строки](https://msdn.microsoft.com/library/077077b4-0f4b-4633-92d6-60b321164cab).  
  
### <a name="to-register-a-category-using-built-in-fonts-and-colors"></a>Регистрация категории с помощью встроенных шрифтов и цветов  
  
1. Создайте особый тип записи реестра категории в следующем расположении:  
  
     [Хклм\софтваре\микрософт \Висуал Studio \\ *\<Visual Studio version>* \Фонтандколорс \\ *\<Category>* ]  
  
     *\<Category>* нелокализованное имя категории.  
  
2. Заполните реестр, чтобы использовать стандартные шрифты и цветовую схему с четырьмя значениями:  
  
    |Имя|Тип|Данные|Описание|  
    |----------|----------|----------|-----------------|  
    |Категория|REG_SZ|Код GUID|Произвольный идентификатор GUID, определяющий категорию, содержащую шрифт и цветовую схему акции.|  
    |Пакет|REG_SZ|Код GUID|{F5E7E71D-1401-11D1-883B-0000F87579D2}<br /><br /> Этот идентификатор GUID используется всеми пакетами VSPackage, которые используют конфигурации шрифтов и цветов по умолчанию.|  
    |NameID|REG_DWORD|ID|Идентификатор ресурса имени локализуемого категории в VSPackage.|  
    |тулвиндовпаккаже|REG_SZ|Код GUID|Идентификатор GUID пакета VSPackage, реализующего <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> интерфейс.|  
  
3. 
  
### <a name="to-initiate-the-use-of-system-provided-fonts-and-colors"></a>Инициация использования предоставляемых системой шрифтов и цветов  
  
1. Создайте экземпляр `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` интерфейса в рамках реализации и инициализации окна.  
  
2. Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> метод, чтобы получить экземпляр интерфейса, `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` соответствующий текущему <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> экземпляру.  
  
3. Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> дважды.  
  
   - Вызовите один раз, указав `VSEDITPROPID_ViewGeneral_ColorCategory` в качестве аргумента.  
  
   - Вызовите один раз, указав `VSEDITPROPID_ViewGeneral_FontCategory` в качестве аргумента.  
  
     При этом устанавливаются и предоставляются службы шрифтов и цветов по умолчанию в качестве свойства окна.  
  
## <a name="example"></a>Пример  
 В следующем примере инициируется использование встроенных шрифтов и цветов.  
  
```  
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
  
## <a name="see-also"></a>См. также:  
 [Использование шрифтов и цветов](../extensibility/using-fonts-and-colors.md)   
 [Получение сведений о шрифтах и цветах для цветовой раскраски текста](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [Доступ к сохраненным параметрам шрифта и цвета](../extensibility/accessing-stored-font-and-color-settings.md)   
 [Общие сведения о шрифтах и цветах](../extensibility/font-and-color-overview.md)
