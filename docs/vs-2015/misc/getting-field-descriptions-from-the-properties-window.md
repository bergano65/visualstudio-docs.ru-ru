---
title: Получение описаний полей из окна свойств | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- Properties window, field descriptions
ms.assetid: 7d92bb6a-b9b9-4cd8-99e9-b5ee129b52a3
caps.latest.revision: 9
manager: jillfra
ms.openlocfilehash: 1d2b152fd7ed517a238f9893320bd0c36035627c
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/15/2019
ms.locfileid: "65703983"
---
# <a name="getting-field-descriptions-from-the-properties-window"></a>Получение описаний полей из окна "Свойства"
В нижней части окна **Свойства** в области описания отображаются сведения, относящиеся к выбранному полю свойства. Эта функция включена по умолчанию. Если необходимо скрыть поле описания, правой кнопкой мыши щелкните окно **Свойства** и выберите пункт **Описание**. При этом также снимается флажок рядом с заголовком **Описание** в окне меню. Чтобы отобразить поле повторно, выполните те же действия для включения пункта **Описание** .  
  
 Сведения в поле "Описание" поступают из <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>. Каждый метод, интерфейс, компонентный класс и т. д. может иметь нелокализованный атрибут `helpstring` в библиотеке типов. **Свойства** окно получает строку из <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A>.  
  
### <a name="to-specify-localized-help-strings"></a>Указание локализованных строк справки  
  
1. Добавьте атрибут `helpstringdll` в инструкцию библиотеки в библиотеке типов (`typelib`).  
  
   > [!NOTE]
   > Этот шаг является необязательным, если библиотека типов находится в файле библиотеки (OLB-файле).  
  
2. Укажите атрибуты `helpstringcontext` для строк. Можно также указать атрибуты `helpstring` .  
  
    Они отличаются от атрибутов `helpfile` и `helpcontext` , которые содержатся в реальных разделах справки в формате CHM.  
  
   Чтобы получить описание, которое будет отображаться для выбранного имени свойства, **свойства** вызовы в окна <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> для выбранного свойства с указанием нужного `lcid` для атрибута Выходная строка. На внутреннем уровне <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> находит DLL-файл, указанный в атрибуте `helpstringdll`, и вызывает в этом файле метод `DLLGetDocumentation` с заданным контекстом и атрибутом `lcid`.  
  
   Подпись и реализация метода `DLLGetDocumentation` выглядят следующим образом.  
  
```  
STDAPI DLLGetDocumentation  
(  
   ITypeLib * /* ptlib */,  
   ITypeInfo * /* ptinfo */,  
   LCID /* lcid */,  
   DWORD dwCtx,  
   BSTR * pbstrHelpString  
);  
```  
  
 Функция `DLLGetDocumentation` должна быть функцией экспорта, определенной в DEF-файле библиотеки DLL.  
  
 На внутреннем уровне создается OLB-файл, который на самом деле является библиотекой DLL. Эта библиотека DLL содержит один ресурс — файл библиотеки типов (TLB-файл) — и одну экспортированную функцию — `DLLGetDocumentation`.  
  
 Что касается OLB-файлов, атрибут `helpstringdll` является необязательным, так как это тот же файл, содержащий сам TLB-файл.  
  
 Таким образом, чтобы строки отображались в области **Описание** , нужно по меньшей мере указать атрибут `helpstring` в библиотеке типов. Если эти строки требуется локализовать, необходимо указать необязательный атрибут `helpstringdll` и обязательный атрибут `helpstringcontext` , а затем реализовать `DLLGetDocumentation`.  
  
 При получении локализованных сведений с помощью атрибута `helpstringcontext` idl и `DLLGetDocumentation`реализовывать дополнительные интерфейсы не нужно.  
  
 Другим способом получения локализованного имени и описания свойства является реализация метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A>. Дополнительные сведения, относящиеся к реализации этого метода, см. в статье [Properties Window Fields and Interfaces](../extensibility/internals/properties-window-fields-and-interfaces.md).  
  
## <a name="see-also"></a>См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [Поля окна свойств и интерфейсы](../extensibility/internals/properties-window-fields-and-interfaces.md)   
 [Расширение свойств](../extensibility/internals/extending-properties.md)   
 [helpstringdll](https://msdn.microsoft.com/library/121271fa-f061-492b-b87f-bbfcf4b02e7b)   
 [helpstring](https://msdn.microsoft.com/library/0401e905-a63e-4fad-98d0-d1efea111966)   
 [helpstringcontext](https://msdn.microsoft.com/library/d4cd135e-d91c-4aa3-9353-8aeb096f52cf)   
 [helpcontext](https://msdn.microsoft.com/library/6fbb022d-a4b7-4989-a02f-7f18a9b0ad96)   
 [helpfile](https://msdn.microsoft.com/library/d75161c1-1363-4019-ae09-e7e3b8a3971e)   
 [lcid](https://msdn.microsoft.com/library/7f248c69-ee1c-42c3-9411-39cf27c9f43d)