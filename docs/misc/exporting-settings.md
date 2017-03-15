---
title: "Экспорт параметров | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDE, экспорт параметров с помощью Managed Package Framework"
  - "Managed Package Framework, экспорт параметров среды"
  - "параметры пользователя [Visual Studio SDK], экспорт с помощью Managed Package Framework"
  - "Параметры IDE, экспорт с помощью Managed Package Framework"
ms.assetid: cb3ddb38-4e75-4f05-a83a-8396345bc36c
caps.latest.revision: 24
caps.handback.revision: 24
manager: "douge"
---
# Экспорт параметров
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] интегрированная среда разработки \(ide\) использует классы, реализующие  <xref:Microsoft.VisualStudio.Shell.IProfileManager> интерфейс и классы, которые зарегистрированы как обслуживать заданный реализацию VSPackage, чтобы сохранить состояние VSPackage.  
  
 Поскольку создает интегрированной среды разработки класс, реализующий <xref:Microsoft.VisualStudio.Shell.IProfileManager> интерфейс для поддержки параметров  <xref:Microsoft.VisualStudio.Shell.IProfileManager> быть реализовано в независимом классе.  
  
> [!NOTE]
>  Не реализуйте <xref:Microsoft.VisualStudio.Shell.IProfileManager> в классе, который реализует  <xref:Microsoft.VisualStudio.Shell.Package>.  
  
### Реализовать экспорт параметров  
  
1.  Объявите класс, реализующий [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] параметры.  
  
     Объявите класс как реализация <xref:Microsoft.VisualStudio.Shell.IProfileManager> интерфейс и предоставляет его с GUID.  
  
    > [!NOTE]
    >  Классы, реализующие <xref:Microsoft.VisualStudio.Shell.IProfileManager> должны также реализует  <xref:System.ComponentModel.IComponent>.  Это делается путем наследования от класса <xref:System.ComponentModel.Component>.  
  
     Примеры.  
  
    ```  
    [Guid("XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX")]  
    internal class MyPackageProfileManager : Component, IProfileManager   
    ```  
  
2.  Убедитесь, что класс, который реализует параметры возвращает правильные сведения о состоянии.  Эта процедура относится к каждому VSPackage, и может включать получить состояние автоматизации, запроса разделы реестра или запросить VSPackage.  
  
     Как правило, например в следующем примере используется реализация <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> метод, который требуется проверить и сведения о состоянии VSPackage стадии.  
  
    > [!NOTE]
    >  <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> метод также вызывается средой разработки, когда он инициализирует VSPackage, он поддерживает.  
  
     В этом случае реализация <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> метод выполняет следующие действия:  
  
    -   Получает доступ к сведениям о состоянии в конфигурации и конфигурации VSPackage, который текущих хранятся в реестре.  
  
        ```vb#  
        Dim mySvc As MyPackageService = TryCast(GetService(GetType(IVSMDMyPackage)), MyPackageService)   
        Dim package As Package = TryCast(GetService(GetType(Package)), Package)   
        Dim rootKey As RegistryKey = package.UserRegistryRoot  
        ```  
  
        ```c#  
        MyPackageService mySvc = GetService(typeof(IVSMDMyPackage)) as MyPackageService;  
        Package package = GetService(typeof(Package)) as Package;  
        RegistryKey rootKey = package.UserRegistryRoot;  
        ```  
  
    -   В зависимости от значения, возвращенного `MakeCurrentSettingTheDefault` метод VSPackage или обновляет параметры реестра с использованием текущего состояния VSPackage или состояния с помощью параметров реестра.  
  
        ```vb#  
        If mySvc.MyPackage.MakeCurrentSettingTheDefault() Then   
            DirectCast(mySvc.MyPackage.packageState, IComPropertyBrowser).SaveState(pbrsKey)   
        Else   
            DirectCast(mySvc.MyPackage.packageState, IComPropertyBrowser).LoadState(pbrsKey)   
        End If  
        ```  
  
        ```c#  
        if (mySvc.MyPackage.MakeCurrentSettingTheDefault()){  
          ((IComPropertyBrowser)mySvc.MyPackage.packageState).SaveState(pbrsKey);  
        }else{  
          ((IComPropertyBrowser)mySvc.MyPackage.packageState).LoadState(pbrsKey);  
        }  
        ```  
  
         Для простоты в этом примере, если `MakeCurrentSettingsTheDefault` метод возвращает  `true`текущее состояние всегда было сброшено значение по умолчанию, которое хранится в реестре.  
  
3.  Убедитесь, что класс, реализующий эти параметры также сохраняет состояние на диск.  
  
     Фактическая запись сведений о состоянии в файл на диске параметров всегда должна быть выполнена реализацией класса <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> метод.  Особенности зависит от реализации операции писателя параметров.  
  
     Однако класс должен получить доступ к сведениям о состоянии и должен использовать предоставленное <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> интерфейс, чтобы сохранять данные в файле параметра.  
  
     Как правило, например в следующем примере реализация <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> метод не проверяет сведения о состоянии.  Проверка выполняется в <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> метод.  Вместо этого реализация просто получает доступ к сведениям о состоянии и записывает ее в данном случае как данные строк.  
  
    ```vb#  
    Dim mySvc As MyPackageService = TryCast(GetService(GetType(MyPackage)), MyPackageService)   
    If mySvc IsNot Nothing Then   
        ' Information is stored in a StateObject   
        Dim myState As StateObject = mySvc.MyPackage.packageState   
        writer.WriteSettingString("PbrsAlpha", (If(myState.SortState = SortState.Alphabetical, "1", "0")))   
        writer.WriteSettingString("PbrsShowDesc", (If(myState.HelpVisible, "1", "0")))   
    End If  
  
    ```  
  
    ```c#  
    MyPackageService mySvc = GetService(typeof(MyPackage)) as MyPackageService;  
    if (mySvc != null) {  
      // Information is stored in a StateObject  
      StateObject myState = mySvc.MyPackage.packageState;  
     writer.WriteSettingString(   
                                "PbrsAlpha",   
                                (myState.SortState == SortState.Alphabetical ? "1" : "0"));  
      writer.WriteSettingString(   
                                "PbrsShowDesc",   
                                (myState.HelpVisible ? "1" : "0"));  
    }  
    ```  
  
     Сведения о реализации следующим образом:  
  
    -   В дополнение к данным, написанным с явно и прозрачному <xref:Microsoft.VisualStudio.Shell.Interop.IVsUserSettings.ExportSettings%2A> реализация метода API также сохраняет параметры  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] сведения о версии.  Таким образом, сохраняется параметры могут быть сравнивается с версии интегрированной среды разработки, сформировавшего их во время импорта параметров.  
  
    -   Значение  `pszSettingName` аргумент, переданный методу  <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> интерфейс должен уникально идентифицировать каждый элемент данных, сохраненный в категории параметров.  
  
        > [!NOTE]
        >  Имена должны быть уникальными в пределах области реализующего класса.  Интегрированная среда разработки использует идентификатор GUID класса, реализующего параметры и значения `pszSettingName` сохраненный идентифицировать каждый параметр.  Если несколько объектов <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter> метод, имеющий одинаковые  `pszSettingName` вызывается значение, исходное значение перезаписывается в файле параметров.  
  
    -   Файл параметров поддерживает случайный доступ к данным, поэтому порядок операций чтения и записи не важен.  В следующем примере порядок операций писателя в реализации <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromXml%2A> метод является обратным по отношению к операций чтения  <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> метод.  
  
    -   Если реализация может данные карты в один из поддерживаемых форматов 4, отсутствие ограничений на объем или каком тип данных можно записать.  
  
        > [!NOTE]
        >  Разделение между труда <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> и  <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> реализация зависит от методов и несколько произвольны.  Например, реализация может быть перезаписана посредством пустой реализации <xref:Microsoft.VisualStudio.Shell.IProfileManager.SaveSettingsToXml%2A> метод и все запросы выполняются в реестре и состояния  <xref:Microsoft.VisualStudio.Shell.IProfileManager.LoadSettingsFromStorage%2A> метод.  
  
4.  Зарегистрируйте параметры, реализующий класс как поддержку VSPackage.  
  
     Примените экземпляр  <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> он построен с помощью  <xref:System.Type> класса, реализующего  <xref:Microsoft.VisualStudio.Shell.IProfileManager> в VSPackage  <xref:Microsoft.VisualStudio.Shell.Package> реализация.  
  
    ```vb#  
    <ProvideProfile(GetType(MyPackageProfileManager), "CoreUI", "MyPackage", 1004, 1004, False)> _   
    <Guid("YYYYYYYY-YYYY-YYYY-YYYY-YYYYYYYYYYYY")> _   
    Class MyPackage   
        Inherits Package   
    End Class  
    ```  
  
    ```c#  
    [ProvideProfile(typeof(MyPackageProfileManager), "CoreUI", "MyPackage", 1004, 1004, false)]  
    [Guid("YYYYYYYY-YYYY-YYYY-YYYY-YYYYYYYYYYYY")]  
    class MyPackage: Package   
    ```  
  
     В этом случае атрибут сообщает интегрированную среду разработки, `MyPackageProfileManager` класс предоставляет реализацию параметров  `MyPackage` класс.  Пользовательский пункт параметры в реестре создается в разделе реестра " HKLM \\ software \\ microsoft \\ VisualStudio \\*Версия*\\ \\ CoreUI\_MyPackage, где UserSettings  *Версия* версия   [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], например 10,0.  
  
     Дополнительные сведения см. в разделах [Поддержка параметров пользователя](../extensibility/internals/support-for-user-settings.md) и <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute>.  
  
## Пример  
 Следующий пример реализует <xref:Microsoft.VisualStudio.Shell.IProfileManager> в классе.  
  
```vb#  
Imports System   
Imports System.Runtime.InteropServices   
Imports Microsoft.VisualStudio.Shell   
Imports Microsoft.VisualStudio.Shell.Interop   
Imports Microsoft.Win32   
Imports myPackageNameSpace   
Namespace myProfileManagerNameSpace  
  
    <Guid("XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX")> _   
    Friend Class MyPackageProfileManager   
        Inherits System.ComponentModel.Component   
        Implements IProfileManager   
        Friend Const m_supportVer As Integer = 8   
        Public Sub SaveSettingsToXml(ByVal writer As IVsSettingsWriter)   
            Dim mySvc As MyPackageService = TryCast(GetService(GetType(MyPackage)), MyPackageService)   
            If mySvc IsNot Nothing Then   
                ' Information is stored in a StateObject.   
                Dim myState As StateObject = mySvc.MyPackage.packageState   
                writer.WriteSettingString("PbrsAlpha", (If(myState.SortState = SortState.Alphabetical, "1", "0")))   
                writer.WriteSettingString("PbrsShowDesc", (If(myState.HelpVisible, "1", "0")))   
            End If   
        End Sub   
  
        Public Sub LoadSettingsFromXml(ByVal reader As IVsSettingsReader)   
  
            Dim pnMajor As Integer, pnMinor As Integer, pnBuild As Integer   
            ' First, check if data is obtained from the correct major version   
            reader.ReadVersion(pnMajor, pnMinor, pnBuild)   
            If pnMajor <> m_supportVer Then   
                reader.ReportError("Unsupported Version")   
            Else   
                Dim mySvc As MyPackageService = TryCast(GetService(GetType(IVSMDMyPackage)), MyPackageService)   
                If mySvc IsNot Nothing Then   
                    Dim value As String   
                    Dim myState As StateObject = mySvc.MyPackage.packageState   
                    reader.ReadSettingString("PbrsShowDesc", value)   
                    ' Not all values must be present.   
                    If value Is Nothing OrElse value = "" Then   
                        reader.ReportError("Unable to Help Visibility Setting")   
                    Else   
                        myState.HelpVisible = Not value.Equals("0")   
                    End If   
                    reader.ReadSettingString("PbrsAlpha", value)   
                    ' Not all values must be present.   
                    If value Is Nothing OrElse value = "" Then   
                        reader.ReportError("Unable to Retrieve Sort Value")   
                    Else   
                        If Not value.Equals("0") Then   
                            myState.SortState = SortState.Alphabetical   
                        Else   
                            myState.SortState = SortState.Categorized   
                        End If   
                    End If   
                End If   
            End If   
        End Sub   
  
        Public Sub SaveSettingsToStorage()   
            Dim mySvc As MyPackageService = TryCast(GetService(GetType(IVSMDMyPackage)), MyPackageService)   
            Dim package As Package = TryCast(GetService(GetType(Package)), Package)   
            Dim rootKey As RegistryKey = package.UserRegistryRoot   
  
            If mySvc.MyPackage.packageState IsNot Nothing Then   
                Using rootKey   
                    Using pbrsKey As RegistryKey = rootKey.CreateSubKey(Me.[GetType]().Name)   
                        Using pbrsKey   
                            DirectCast(mySvc.MyPackage.packageState, IComPropertyBrowser).SaveState(pbrsKey)   
                        End Using   
                    End Using   
                End Using   
            End If   
        End Sub   
  
        Public Sub LoadSettingsFromStorage()   
            Dim mySvc As MyPackageService = TryCast(GetService(GetType(IVSMDMyPackage)), MyPackageService)   
            Dim package As Package = TryCast(GetService(GetType(Package)), Package)   
            Dim rootKey As RegistryKey = package.UserRegistryRoot   
            Using rootKey   
                Dim pbrsKey As RegistryKey = rootKey.OpenSubKey(Me.[GetType]().Name)   
                If pbrsKey IsNot Nothing Then   
                    Using pbrsKey   
                        If mySvc.MyPackage.MakeCurrentSettingTheDefault() Then   
                            DirectCast(mySvc.MyPackage.packageState, IComPropertyBrowser).SaveState(pbrsKey)   
                        Else   
                            DirectCast(mySvc.MyPackage.packageState, IComPropertyBrowser).LoadState(pbrsKey)   
                        End If   
                    End Using   
                End If   
            End Using   
        End Sub   
    End Class   
End Namespace   
  
Convert C# to VB.NET  
  
```  
  
```c#  
namespace myProfileManagerNameSpace  {  
  
  using System;  
  using System.Runtime.InteropServices;  
  using Microsoft.VisualStudio.Shell;  
  using Microsoft.VisualStudio.Shell.Interop;  
  using Microsoft.Win32;  
  using myPackageNameSpace;  
  
  [Guid("XXXXXXXX-XXXX-XXXX-XXXX-XXXXXXXXXXXX")]  
  internal class MyPackageProfileManager : System.ComponentModel.Component , IProfileManager {  
    internal const int m_supportVer = 8;  
    public void SaveSettingsToXml(IVsSettingsWriter writer) {  
      MyPackageService mySvc = GetService(typeof(MyPackage)) as MyPackageService;  
      if (mySvc != null) {  
        // Information is stored in a StateObject.  
        StateObject myState = mySvc.MyPackage.packageState;  
        writer.WriteSettingString(   
                                  "PbrsAlpha",   
                                  (myState.SortState == SortState.Alphabetical ? "1" : "0"));  
        writer.WriteSettingString(   
                                  "PbrsShowDesc",   
                                  (myState.HelpVisible ? "1" : "0"));  
      }  
    }  
  
    public void LoadSettingsFromXml(IVsSettingsReader reader)  
    {  
  
      int pnMajor, pnMinor, pnBuild;  
      // First, check if data is obtained from the correct major version   
      reader.ReadVersion(pnMajor, pnMinor, pnBuild);  
      if (pnMajor != m_supportVer){  
        reader.ReportError("Unsupported Version");  
      }else{  
        MyPackageService mySvc = GetService(typeof(IVSMDMyPackage)) as MyPackageService;  
        if (mySvc != null){  
          string value;  
          StateObject myState = mySvc.MyPackage.packageState;  
          reader.ReadSettingString("PbrsShowDesc", out value);  
          // Not all values must be present.  
          if (value == null || value == ""){  
              reader.ReportError("Unable to Help Visibility Setting");  
          }else{  
            myState.HelpVisible = !value.Equals("0");  
          }  
          reader.ReadSettingString("PbrsAlpha", out value);  
          // Not all values must be present.  
          if (value == null || value == ""){  
              reader.ReportError("Unable to Retrieve Sort Value");  
          }else{  
            if (!value.Equals("0")){  
              myState.SortState = SortState.Alphabetical;  
            }else{  
              myState.SortState = SortState.Categorized;  
            }  
          }  
        }  
      }  
    }  
  
    public void SaveSettingsToStorage() {  
      MyPackageService mySvc = GetService(typeof(IVSMDMyPackage)) as MyPackageService;  
      Package package = GetService(typeof(Package)) as Package;  
      RegistryKey rootKey = package.UserRegistryRoot;  
  
      if (mySvc.MyPackage.packageState != null) {  
        using (rootKey) {  
          using(RegistryKey pbrsKey = rootKey.CreateSubKey(this.GetType().Name)) {  
            using (pbrsKey) {  
              ((IComPropertyBrowser)mySvc.MyPackage.packageState).SaveState(pbrsKey);  
            }  
          }  
        }  
      }  
    }  
  
    public void LoadSettingsFromStorage() {  
      MyPackageService mySvc = GetService(typeof(IVSMDMyPackage)) as MyPackageService;  
      Package package = GetService(typeof(Package)) as Package;  
      RegistryKey rootKey = package.UserRegistryRoot;  
      using (rootKey) {  
        RegistryKey pbrsKey = rootKey.OpenSubKey(this.GetType().Name);  
        if (pbrsKey != null) {  
          using (pbrsKey) {  
            if (mySvc.MyPackage.MakeCurrentSettingTheDefault()){  
              ((IComPropertyBrowser)mySvc.MyPackage.packageState).SaveState(pbrsKey);  
            }else{  
              ((IComPropertyBrowser)mySvc.MyPackage.packageState).LoadState(pbrsKey);  
            }  
          }  
        }  
      }  
    }  
  }  
}  
```  
  
## См. также  
 <xref:Microsoft.VisualStudio.Shell.IProfileManager>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsWriter>   
 [Импорт параметров](/visual-cpp/misc/importing-settings)   
 [Поддержка параметров пользователя](../extensibility/internals/support-for-user-settings.md)