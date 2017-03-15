---
title: "Практическое руководство: доступ к встроенных шрифтов и цветовой схемы | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "шрифты, доступ к встроенной"
  - "шрифт и цвет элемента управления [Visual Studio SDK] категории"
  - "цвета, доступ к встроенной схемы"
ms.assetid: 6905845e-e88e-4805-adcf-21da39108ec7
caps.latest.revision: 23
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 23
---
# Практическое руководство: доступ к встроенных шрифтов и цветовой схемы
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Среда разработки Visual Studio \(IDE\) имеется схема шрифтов и цветов, связанный с окном редактора. Можно получить доступ к этой схемы через <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> интерфейса.  
  
 Использование встроенных шрифтов и цветов схемы, VSPackage выполните следующие действия.  
  
-   Определение категории для использования со службой шрифты и цвета по умолчанию.  
  
-   Категория зарегистрироваться на сервере по умолчанию шрифты и цвета.  
  
-   Рекомендуем IDE отдельного окна использование встроенных элементов и категории с помощью `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` и `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` интерфейсов.  
  
 Интегрированная среда разработки использует полученный категории как дескриптор окна. Имя категории отображается в **Показать параметры для:** раскрывающегося списка в **шрифты и цвета** страницу свойств.  
  
### Для определения категории с помощью встроенных шрифтов и цветов  
  
1.  Создайте произвольный идентификатор GUID.  
  
     Идентификатор GUID используется для уникальной идентификации категории**.** Эта категория повторно используется спецификация цветов и шрифтов по умолчанию интегрированной среды разработки.  
  
    > [!NOTE]
    >  При получении данных шрифтов и цветов с <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> или других интерфейсов VSPackages использовать этот идентификатор GUID для ссылки на встроенные сведения.  
  
2.  Имя категории добавляются в таблицу строки в файл ресурсов \(с расширением RC\) VSPackage, таким образом, можно локализовать, при необходимости, при отображении в Интегрированной среде разработки.  
  
     Для получения дополнительной информации см. [Adding or Deleting a String](/visual-cpp/windows/adding-or-deleting-a-string).  
  
### Чтобы зарегистрировать категории, используя встроенные шрифты и цвета  
  
1.  Создайте специальный тип категории записи реестра в следующем расположении:  
  
     \[HKLM\\SOFTWARE\\Microsoft \\Visual Studio\\*\< версия Visual Studio \>*\\FontAndColors\\*\< Category \>*\]  
  
     *\< category \>* нелокализованное имя категории.  
  
2.  Добавить в реестр для использования стандартных шрифтов и цветовой схемы с четырьмя значениями:  
  
    |Имя|Тип|Данные|Описание|  
    |---------|---------|------------|--------------|  
    |Категория|REG\_SZ|GUID|Произвольный GUID, определяющий категорию, которая содержит акций шрифт и цветовую схему.|  
    |Пакет|REG\_SZ|GUID|{F5E7E71D\-1401\-11D1\-883B\-0000F87579D2}<br /><br /> Этот идентификатор GUID используется все пакеты VSPackage, используйте параметры шрифта и цвета по умолчанию.|  
    |Идентификатора имени|REG\_DWORD|Идентификатор|Идентификатор ресурса имени категории локализуемых в VSPackage.|  
    |ToolWindowPackage|REG\_SZ|GUID|Идентификатор GUID реализации VSPackage <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> интерфейса.|  
  
3.  
  
### Чтобы начать использование системных шрифтов и цветов  
  
1.  Создайте экземпляр `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` интерфейса как часть реализации и инициализации окна.  
  
2.  Вызов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> метод, чтобы получить экземпляр `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` интерфейс, соответствующий текущему <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> экземпляра.  
  
3.  Вызов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A> дважды.  
  
    -   После вызова с `VSEDITPROPID_ViewGeneral_ColorCategory`в качестве аргумента.  
  
    -   После вызова с `VSEDITPROPID_ViewGeneral_FontCategory` в качестве аргумента.  
  
     Это задает и предоставляет службы шрифты и цвета по умолчанию в качестве свойства окна.  
  
## Пример  
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
  
## См. также  
 [Шрифты и цвета](../extensibility/using-fonts-and-colors.md)   
 [Получение шрифта и цвет шрифта для текста цветом](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [Доступ к хранимой шрифта и цветов](../extensibility/accessing-stored-font-and-color-settings.md)   
 [Обзор цвета и шрифта](../extensibility/font-and-color-overview.md)