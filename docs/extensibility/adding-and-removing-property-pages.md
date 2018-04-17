---
title: Добавление и удаление страниц свойств | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- property pages, adding
- property pages, project subtypes
- property pages, removing
ms.assetid: 34853412-ab8a-4caa-9601-7d0727b2985d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8a8130056437bf35a1617544ae7d1ecfb9068946
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="adding-and-removing-property-pages"></a>Добавление и удаление страниц свойств
Конструктор проектов предоставляет централизованно управлять свойствами проекта, параметры и ресурсы в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Он представляется в виде одного окна в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] интегрированной среде разработки (IDE) и содержит ряд области справа, осуществляется с помощью вкладок в левой части экрана. Области (часто обозначается как страницы свойств) в конструкторе проектов различаются по типу проекта и языку. Конструктор проектов можно осуществить с помощью **свойства** на **проекта** меню.  
  
 Подтип проекта часто необходимо отобразить дополнительные страницы свойств в конструкторе проектов. Аналогично некоторые подтипы проекта может потребоваться удалить встроенного свойства страницы. Для выполнения любого, необходимо реализовать ваш проект подтип <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> интерфейс и Переопределите <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> метод. Переопределение этого метода и используя `propId` параметр, содержащий одно из значений <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> перечисления, можно фильтровать, добавить или удалить свойства проекта. Например может потребоваться добавить страницу на страницах свойств в зависимости от конфигурации. Для этого необходимо отфильтровать страницы свойств в зависимости от конфигурации, а затем добавьте новую страницу в существующий список.  
  
## <a name="adding-and-removing-property-pages-in-project-designer"></a>Добавление и удаление страниц свойств в конструкторе проектов  
  
#### <a name="to-remove-a-property-page-in-project-designer"></a>Для удаления страницы свойств в конструкторе проектов  
  
1.  Переопределить `GetProperty(uint itemId, int propId, out object property)` метод для фильтрации страницы свойств и получить `clsids` списка.  
  
    ```vb  
    Protected Overrides int GetProperty(uint itemId, int propId, out object property)  
    Protected Overrides Function GetProperty(ByVal itemId As UInteger, ByVal propId As Integer, ByRef [property] As Object) As Integer  
        'Use propId to filter configuration-independent property pages.  
        Select Case propId  
            ....   
            Case CInt(Fix(__VSHPROPID2.VSHPROPID_PropertyPagesCLSIDList))  
                'Get a semicolon-delimited list of clsids of the configuration-independent property pages  
                ErrorHandler.ThrowOnFailure(MyBase.GetProperty(itemId, propId, [property]))  
                   Dim propertyPagesList As String = ((String)[property]).ToUpper(CultureInfo.InvariantCulture)  
                'Remove the property page here  
                   ....  
            ....  
        End Select  
            ....   
        Return MyBase.GetProperty(itemId, propId, [property])  
    End Function  
  
    ```  
  
    ```csharp  
    protected override int GetProperty(uint itemId, int propId, out object property)  
    {  
        //Use propId to filter configuration-independent property pages.  
        switch (propId)  
        {  
            . . . .  
  
            case (int)__VSHPROPID2.VSHPROPID_PropertyPagesCLSIDList:  
                {  
                    //Get a semicolon-delimited list of clsids of the configuration-independent property pages  
                    ErrorHandler.ThrowOnFailure(base.GetProperty(itemId, propId, out property));  
                    string propertyPagesList = ((string)property).ToUpper(CultureInfo.InvariantCulture);  
                    //Remove the property page here  
                    . . . .  
                }  
             . . . .  
         }  
            . . . .  
        return base.GetProperty(itemId, propId, out property);  
    }  
    ```  
  
2.  Удалить **события построения** получить страницу из `clsids` списка.  
  
    ```vb  
    Private buildEventsPageGuid As String = "{1E78F8DB-6C07-4D61-A18F-7514010ABD56}"  
    Private index As Integer = propertyPagesList.IndexOf(buildEventsPageGuid)  
    If index <> -1 Then  
        ' GUIDs are separated by ';' so if you remove the last GUID, also remove the last ';'  
        Dim index2 As Integer = index + buildEventsPageGuid.Length + 1  
        If index2 >= propertyPagesList.Length Then  
            propertyPagesList = propertyPagesList.Substring(0, index).TrimEnd(";"c)  
        Else  
            propertyPagesList = propertyPagesList.Substring(0, index) + propertyPagesList.Substring(index2)  
        End If  
    End If  
    'New property value  
    property = propertyPagesList  
    ```  
  
    ```csharp  
    string buildEventsPageGuid = "{1E78F8DB-6C07-4D61-A18F-7514010ABD56}";  
    int index = propertyPagesList.IndexOf(buildEventsPageGuid);  
    if (index != -1)  
    {  
        // GUIDs are separated by ';' so if you remove the last GUID, also remove the last ';'  
        int index2 = index + buildEventsPageGuid.Length + 1;  
        if (index2 >= propertyPagesList.Length)  
            propertyPagesList = propertyPagesList.Substring(0, index).TrimEnd(';');  
        else  
            propertyPagesList = propertyPagesList.Substring(0, index) + propertyPagesList.Substring(index2);  
    }  
    //New property value  
    property = propertyPagesList;  
    ```  
  
#### <a name="to-add-a-property-page-in-project-designer"></a>Добавление страницы свойств в конструкторе проектов  
  
1.  Создание страницы свойств, которые требуется добавить.  
  
    ```vb  
    Class DeployPropertyPage  
            Inherits Form  
            Implements Microsoft.VisualStudio.OLE.Interop.IPropertyPage  
        'Summary: Return a stucture describing your property page.  
        ....   
        Public Sub GetPageInfo(ByVal pPageInfo As Microsoft.VisualStudio.OLE.Interop.PROPPAGEINFO())  
            Dim info As PROPPAGEINFO = New PROPPAGEINFO()  
            info.cb = CUInt(Marshal.SizeOf(GetType(PROPPAGEINFO)))  
            info.dwHelpContext = 0  
            info.pszDocString = Nothing  
            info.pszHelpFile = Nothing  
            info.pszTitle = "Deployment" 'Assign tab name  
            info.SIZE.cx = Me.Size.Width  
            info.SIZE.cy = Me.Size.Height  
            If Not pPageInfo Is Nothing AndAlso pPageInfo.Length > 0 Then  
                pPageInfo(0) = info  
            End If  
        End Sub  
    End Class  
    ```  
  
    ```csharp  
    class DeployPropertyPage : Form, Microsoft.VisualStudio.OLE.Interop.IPropertyPage  
    {  
        . . . .   
        //Summary: Return a stucture describing your property page.  
        public void GetPageInfo(Microsoft.VisualStudio.OLE.Interop.PROPPAGEINFO[] pPageInfo)  
        {  
            PROPPAGEINFO info = new PROPPAGEINFO();  
            info.cb = (uint)Marshal.SizeOf(typeof(PROPPAGEINFO));  
            info.dwHelpContext = 0;  
            info.pszDocString = null;  
            info.pszHelpFile = null;  
            info.pszTitle = "Deployment";  //Assign tab name  
            info.SIZE.cx = this.Size.Width;  
            info.SIZE.cy = this.Size.Height;  
            if (pPageInfo != null && pPageInfo.Length > 0)  
                pPageInfo[0] = info;  
        }  
    }  
    ```  
  
2.  Зарегистрируйте новую страницу свойств.  
  
    ```vb  
    <MSVSIP.ProvideObject(GetType(DeployPropertyPage), RegisterUsing = RegistrationMethod.CodeBase)>  
    ```  
  
    ```csharp  
    [MSVSIP.ProvideObject(typeof(DeployPropertyPage), RegisterUsing = RegistrationMethod.CodeBase)]  
    ```  
  
3.  Переопределить `GetProperty(uint itemId, int propId, out object property)` метод для фильтрации страницы свойств, получить `clsids` списка и добавьте новую страницу свойств.  
  
    ```vb  
    Protected Overrides Function GetProperty(ByVal itemId As UInteger, ByVal propId As Integer, ByRef [property] As Object) As Integer  
        'Use propId to filter configuration-dependent property pages.  
        Select Case propId  
            ....   
            case CInt(Fix(__VSHPROPID2.VSHPROPID_CfgPropertyPagesCLSIDList)):  
                'Get a semicolon-delimited list of clsids of the configuration-dependent property pages.  
                ErrorHandler.ThrowOnFailure(MyBase.GetProperty(itemId, propId, [property]))  
                'Add the Deployment property page.  
                [property] &= ";"c + GetType(DeployPropertyPage).GUID.ToString("B")  
        End Select  
            ....   
            Return MyBase.GetProperty(itemId, propId, [property])  
    End Function  
    ```  
  
    ```csharp  
    protected override int GetProperty(uint itemId, int propId, out object property)  
    {  
        //Use propId to filter configuration-dependent property pages.  
        switch (propId)  
        {  
            . . . .  
            case (int)__VSHPROPID2.VSHPROPID_CfgPropertyPagesCLSIDList:  
                {  
                    //Get a semicolon-delimited list of clsids of the configuration-dependent property pages.  
                    ErrorHandler.ThrowOnFailure(base.GetProperty(itemId, propId, out property));  
                    //Add the Deployment property page.  
                    property += ';' + typeof(DeployPropertyPage).GUID.ToString("B");  
                }  
         }  
            . . . .  
        return base.GetProperty(itemId, propId, out property);  
    }  
    ```  
  
> [!NOTE]
>  Все примеры кода, приведенные в этом разделе являются частью большего примера, в [примеры VSSDK](http://aka.ms/vs2015sdksamples).  
  
## <a name="see-also"></a>См. также  
 [Подтипы проектов](../extensibility/internals/project-subtypes.md)