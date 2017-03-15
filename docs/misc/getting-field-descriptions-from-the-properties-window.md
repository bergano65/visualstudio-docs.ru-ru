---
title: "Получение описаний полей из окна &quot;Свойства&quot; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "окно "Свойства", описания полей"
ms.assetid: 7d92bb6a-b9b9-4cd8-99e9-b5ee129b52a3
caps.latest.revision: 9
caps.handback.revision: 9
manager: "douge"
---
# Получение описаний полей из окна &quot;Свойства&quot;
В нижней части окна **Свойства** в области описания отображаются сведения, относящиеся к выбранному полю свойства. Эта функция включена по умолчанию. Если необходимо скрыть поле описания, правой кнопкой мыши щелкните окно **Свойства** и выберите пункт **Описание**. При этом также снимается флажок рядом с заголовком **Описание** в окне меню. Чтобы отобразить поле повторно, выполните те же действия для включения пункта **Описание**.  
  
 Сведения в поле "Описание" поступают из <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>. Каждый метод, интерфейс, компонентный класс и т. д. может иметь нелокализованный атрибут `helpstring` в библиотеке типов. Окно **Свойства** получает строку из <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A>.  
  
### Указание локализованных строк справки  
  
1.  Добавьте атрибут `helpstringdll` в инструкцию библиотеки в библиотеке типов \(`typelib`\).  
  
    > [!NOTE]
    >  Этот шаг является необязательным, если библиотека типов находится в файле библиотеки \(OLB\-файле\).  
  
2.  Укажите атрибуты `helpstringcontext` для строк. Можно также указать атрибуты `helpstring`.  
  
     Они отличаются от атрибутов `helpfile` и `helpcontext`, которые содержатся в реальных разделах справки в формате CHM.  
  
 Чтобы получить описание, которое будет отображаться для выбранного имени свойства, окно **Свойства** вызывает <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> для выбранного свойства с указанием нужного атрибута `lcid` для выходной строки. На внутреннем уровне <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> находит DLL\-файл, указанный в атрибуте `helpstringdll`, и вызывает в этом файле метод `DLLGetDocumentation` с заданным контекстом и атрибутом `lcid`.  
  
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
  
 Функция `DLLGetDocumentation` должна быть функцией экспорта, определенной в DEF\-файле библиотеки DLL.  
  
 На внутреннем уровне создается OLB\-файл, который на самом деле является библиотекой DLL. Эта библиотека DLL содержит один ресурс — файл библиотеки типов \(TLB\-файл\) — и одну экспортированную функцию — `DLLGetDocumentation`.  
  
 Что касается OLB\-файлов, атрибут `helpstringdll` является необязательным, так как это тот же файл, содержащий сам TLB\-файл.  
  
 Таким образом, чтобы строки отображались в области **Описание**, нужно по меньшей мере указать атрибут `helpstring` в библиотеке типов. Если эти строки требуется локализовать, необходимо указать необязательный атрибут `helpstringdll` и обязательный атрибут `helpstringcontext`, а затем реализовать `DLLGetDocumentation`.  
  
 При получении локализованных сведений с помощью атрибута `helpstringcontext` idl и `DLLGetDocumentation` реализовывать дополнительные интерфейсы не нужно.  
  
 Другим способом получения локализованного имени и описания свойства является реализация метода <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A>. Дополнительные сведения, относящиеся к реализации этого метода, см. в статье [Поля окна свойств и интерфейсы](../extensibility/internals/properties-window-fields-and-interfaces.md).  
  
## См. также  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [Поля окна свойств и интерфейсы](../extensibility/internals/properties-window-fields-and-interfaces.md)   
 [Расширение свойств](../extensibility/internals/extending-properties.md)   
 [helpstringdll](/visual-cpp/windows/helpstringdll)   
 [helpstring](/visual-cpp/windows/helpstring)   
 [helpstringcontext](/visual-cpp/windows/helpstringcontext)   
 [helpcontext](/visual-cpp/windows/helpcontext)   
 [helpfile](/visual-cpp/windows/helpfile)   
 [lcid](/visual-cpp/windows/lcid)