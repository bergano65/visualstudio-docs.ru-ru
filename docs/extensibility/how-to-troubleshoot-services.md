---
title: "Практическое руководство: Устранение неполадок служб | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Устранение неполадок служб"
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Практическое руководство: Устранение неполадок служб
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Существует несколько распространенных проблем, которые могут возникнуть при попытке получения службы:  
  
-   Служба не зарегистрирована на [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Типом интерфейса, а не тип службы, запрошенную службу.  
  
-   VSPackage, запрашивающего службу не был размещен.  
  
-   Используется неправильный доступ к службе.  
  
 Если запрошенная служба недоступна, вызов <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> возвращает значение null. Следует всегда тестировать после выполнения запроса службы со значением NULL:  
  
```c#  
IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog; if (log == null) return;  
```  
  
### Устранение неполадок со службой  
  
1.  Проверьте системный реестр для просмотра ли службы был правильно зарегистрирован. Для получения дополнительной информации см. [Регистрация служб](../misc/registering-services.md).  
  
     В следующем фрагменте файла .reg показано, как могут быть зарегистрированы SVsTextManager службы:  
  
    ```  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}] @="{F5E7E720-1401-11d1-883B-0000F87579D2}" "Name"="SVsTextManager"  
    ```  
  
     В приведенном выше примере номер версии — версия [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], например 12.0 и 14.0 {F5E7E71D\-1401\-11d1\-883B\-0000F87579D2} ключ — это идентификатор службы \(SID\) службы SVsTextManager, и значение по умолчанию {F5E7E720\-1401\-11d1\-883B\-0000F87579D2} является GUID VSPackage, который предоставляет службу диспетчера текст пакета.  
  
2.  Используйте тип службы, а не типа интерфейса, при вызове GetService. При запросе службы из [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], <xref:Microsoft.VisualStudio.Shell.Package> извлекает идентификатор GUID типа. Не удалось найти службу, если выполняются следующие условия:  
  
    1.  Тип интерфейса, передается GetService вместо типа службы.  
  
    2.  Идентификатор GUID не прямо назначенному элементу интерфейса. Таким образом система создает GUID по умолчанию для объекта при необходимости.  
  
3.  Убедитесь, что размещения VSPackage, запрашивающего службу.[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] узлы VSPackage после ее создания и перед вызовом метода <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>.  
  
     Если у вас есть код в конструктор VSPackage, который нуждается в обслуживании, переместите ее в метод Initialize.  
  
4.  Убедитесь, что вы используете правильный доступ к службе.  
  
     Не все поставщики услуг индивидуальны. Поставщик услуг, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] передается в окне инструментов отличается от передачей VSPackage. Поставщик службы окна средства знает о <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>, но не знает о <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>. Можно вызвать метод <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> для получения от поставщика услуг VSPackage из окна инструментов.  
  
     Если окно инструментов содержит пользовательский элемент управления или любой другой контейнер элемента управления, контейнер будет размещаться по модели компонентов Windows и не будет иметь доступ к любому [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] служб. Можно вызвать метод <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> для получения поставщика услуг VSPackage из контейнера элемента управления.  
  
## См. также  
 [Список доступных служб](../extensibility/internals/list-of-available-services.md)   
 [Использование и предоставления услуг](../extensibility/using-and-providing-services.md)   
 [Основы службы](../extensibility/internals/service-essentials.md)