---
title: Обеспечение поддержки версий в пользовательских проектах | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5233d3ff-6e89-4401-b449-51b4686becca
caps.latest.revision: 33
manager: douge
ms.openlocfilehash: 164a56973ac35220a0efd7e85da2f0a074b88b3c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47558628"
---
# <a name="making-custom-projects-version-aware"></a>Обеспечение поддержки версий в пользовательских проектах
В своей системе пользовательских проектов вы можете разрешить проектам данного типа загружаться в нескольких версиях Visual Studio. Вы также можете запретить проектам этого типа загружаться в более ранней версии Visual Studio. Кроме того, можно обеспечить идентификацию проекта для более поздней версии, если этот проекта необходимо восстановить, преобразовать или включить в список устаревших.  
  
## <a name="allowing-projects-to-load-in-multiple-versions"></a>Разрешение загрузки проектов в нескольких версиях  
 Можно изменить большинство проектов, которые были созданы в [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] с пакетом обновления 1 или более поздней версии, чтобы работать в нескольких версиях.  
  
 Перед загрузкой проекта Visual Studio вызывает <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly%2A> метод, чтобы определить, можно ли обновить проект. Если проект можно обновить, `UpgradeProject_CheckOnly` метод устанавливает флаг, который приводит к последующему вызову <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory.UpgradeProject%2A> метод для обновления проекта. Несовместимые проекты не могут быть обновлены, поэтому метод `UpgradeProject_CheckOnly` сначала должен проверить совместимость проекта, как описано в предыдущем разделе.  
  
 Как автор системы проектов реализуйте метод `UpgradeProject_CheckOnly` (при помощи интерфейса `IVsProjectUpgradeViaFactory4` ), чтобы обеспечить проверку возможности обновления для пользователей этой системы. Когда пользователь открывает проект, вызывается этот метод, чтобы определить, нуждается ли проект в исправлении перед его загрузкой. Требования возможного обновления перечислены в разделе `VSPUVF_REPAIRFLAGS`, и они включают следующие возможности.  
  
1.  `SPUVF_PROJECT_NOREPAIR`: Исправление не требуется.  
  
2.  `VSPUVF_PROJECT_SAFEREPAIR`: Делает проект совместимым с более ранней версией без проблем, с которыми вы может сталкиваться в предыдущих версиях продукта.  
  
3.  `VSPUVF_PROJECT_UNSAFEREPAIR`: Делает проект обратную совместимость, но с некоторым риском возникновения проблем, которые вы могли сталкиваться в предыдущих версиях продукта. Например, проект не будет совместимым, если он зависит от разных версий пакета SDK.  
  
4.  `VSPUVF_PROJECT_ONEWAYUPGRADE`: Делает проект несовместимым с более ранней версии.  
  
5.  `VSPUVF_PROJECT_INCOMPATIBLE`: Указывает, что текущая версия не поддерживает этот проект.  
  
6.  `VSPUVF_PROJECT_DEPRECATED`: Указывает, что этот проект больше не поддерживается.  
  
> [!NOTE]
>  Чтобы избежать путаницы, не сочетайте флаги обновления при их установке. Например, не следует создавать неоднозначное состояние обновления, такое как `VSPUVF_PROJECT_SAFEREPAIR | VSPUVF_PROJECT_DEPRECATED`.  
  
 Версии проектов могут реализовывать метод `UpgradeProjectFlavor_CheckOnly` функции из интерфейса `IVsProjectFlavorUpgradeViaFactory2` . Чтобы эта функция работала, реализация `IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly` , упоминавшаяся выше, должна ее вызывать. Этот вызов уже реализован в базовой системе проектов Visual Basic или C#. Действие этой функции позволяет версиям проектов помимо условий базовой системы проектов определять требования к обновлению проекта. В диалоговом окне совместимости показывается наиболее серьезное из этих двух требований.  
  
 Когда Visual Studio выполняет проверку обновления, он предоставляет средство ведения журнала, а не значение NULL, как в предыдущих версиях Visual Studio. Средство ведения журнала позволяет системам проектов и версиям проектов предоставлять дополнительные сведения, которые помогают вам понять природу изменений, необходимых для правильной загрузки более старых проектов. Вместо диалоговых окон рекомендуется использовать средство ведения журнала, чтобы предоставлять дополнительные сведения. Дополнительные сведения см. в разделе [The Upgrade Logger](../misc/making-custom-projects-version-aware.md#BKMK_UpgradeLogger) далее в этом разделе.  
  
 Для управляемых реализаций интерфейсы обновления проектов доступны в сборке взаимодействия Microsoft.VisualStudio.Shell.Interop.11.0.dll.  
  
 Метод `UpgradeProject` может определить, будут ли вносимые им изменения запрещать загрузку проекта в предыдущей версии Visual Studio. Если это так, то метод помечает проект как несовместимый. Чтобы понять, каким образом проект помечается как несовместимый, см. в разделе [помечая проект как несовместимый](../misc/making-custom-projects-version-aware.md#BKMK_Incompat) ранее в этом разделе. Рекомендуется после появления этого диалогового окна помечать проект как несовместимый путем вызова метода `IVsAppCompat.BreakAssetCompatibility` напрямую, не вызывая предварительно метод `IVsAppCompat.AskForUserConsentToBreakAssetCompat` , так как диалоговое окно не нужно отображать дважды.  
  
 Ниже приведен общий пример того, как вмешательство пользователя может привести к несовместимости. Если проект был создан в более ранней версии и текущая версия определяет, что требуется обновление, Visual Studio отображает диалоговое окно с запросом у пользователя разрешения на внесение изменений. Если пользователь соглашается, проект изменяется, а затем загружается. Если затем решение закрывается и снова открывается в более ранней версии, односторонне обновленный проект будет несовместим и не загрузится. Если проекту требовалось только исправление (вместо обновления), исправленный проект по-прежнему будет открываться в обеих версиях.  
  
##  <a name="BKMK_Incompat"></a> Пометка проекта как несовместимого  
 Проект можно пометить как несовместимый с более ранними версиями Visual Studio.  Предположим, что вы создаете проект, использующий компонент .NET Framework 4.5. Поскольку этот проект не может быть построен [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)], его можно пометить как несовместимый, чтобы предотвратить попытки загрузить его в этой версии.  
  
 Компонент, который добавляет несовместимую функцию, отвечает за пометку проекта как несовместимого. Компонент должен иметь доступ к <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> интерфейс, который представляет интересующие проекты.  
  
#### <a name="to-mark-a-project-as-incompatible"></a>Пометка проекта как несовместимого  
  
1.  В компоненте получите интерфейс `IVsAppCompat` из глобальной службы SVsSolution.  
  
     Дополнительные сведения см. в разделе <xref:Microsoft.VisualStudio.Shell.Interop.SVsSolution>.  
  
2.  Вызовите в этом компоненте метод `IVsAppCompat.AskForUserConsentToBreakAssetCompat`и передайте в него массив интерфейсов `IVsHierarchy` , представляющих интересующие проекты.  
  
     Этот метод имеет следующую сигнатуру:  
  
    ```  
    HRESULT AskForUserConsentToBreakAssetCompat([in] SAFEARRAY(IVsHierarchy*) sarrProjectHierarchies)  
  
    ```  
  
     Если вы реализуете этот код, будет отображаться диалоговое окно совместимости проекта. Это диалоговое окно будет запрашивать у пользователя разрешение на пометку всех указанных проектов как несовместимых. Если пользователь соглашается, метод `AskForUserConsentToBreakAssetCompat` возвращает значение `S_OK`. В противном случае `AskForUserConsentToBreakAssetCompat` возвращает значение `OLE_E_PROMPTSAVECANCELLED`.  
  
    > [!WARNING]
    >  В большинстве случаев массив `IVsHierarchy` будет содержать только один элемент.  
  
3.  Если метод `AskForUserConsentToBreakAssetCompat` возвращает `S_OK`, компонент выполняет или принимает изменения, которые прерывают совместимость.  
  
4.  Вызовите в своем компоненте метод `IVsAppCompat.BreakAssetCompatibility` для каждого проекта, который нужно пометить как несовместимый. Этот компонент может установить в качестве значения параметра `lpszMinimumVersion` определенную минимальную версию, чтобы Visual Studio не приходилось искать в реестре строку текущей версии. При таком подходе уменьшается опасность случайного задания компонентом более высокого значения версии в будущем, если в то время в реестре будет указана более поздняя текущая версия. Если установлено более высокое значение, Visual Studio не сможет открыть проект.  
  
     Этот метод имеет следующую сигнатуру:  
  
    ```  
    HRESULT BreakAssetCompatibility([in] IVsHierarchy * pProjHier), [in] LPCOLESTR lpszMinimumVersion);  
  
    ```  
  
     Если компонент устанавливает для параметра `lpszMinimumVersion` значение NULL, метод `BreakAssetCompatibility` вызывает метод `IVsAppCompat.GetCurrentDesignTimeCompatVersion` , чтобы получить строку, представляющую текущую версию Visual Studio.  
  
     Этот метод имеет следующую сигнатуру:  
  
    ```  
    HRESULT GetCurrentDesignTimeCompatVersion([out] BSTR * pbstrCurrentDesignTimeCompatVersion)  
    ```  
  
     Затем метод BreakAssetCompatibility вызывает метод `IVsHierarchy.SetProperty` , чтобы задать в качестве значения корневого свойства `VSHPROPID_MinimumDesignTimeCompatVersion` строку версии, полученную на предыдущем шаге.  
  
     Дополнительные сведения см. в разделе <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.SetProperty%2A>.  
  
> [!IMPORTANT]
>  Вы должны реализовать свойство `VSHPROPID_MinimumDesignTimeCompatVersion` , чтобы пометить проект как совместимый или несовместимый. Например, если система проектов использует файл проекта MSBuild, добавьте в этот файл проекта свойство сборки `<MinimumVisualStudioVersion>` , имеющее значение, равное значению соответствующего свойства `VSHPROPID_MinimumDesignTimeCompatVersion` .  
  
## <a name="detecting-whether-a-project-is-incompatible"></a>Определение несовместимости проекта  
 Загрузка проекта, который несовместим с текущей версией Visual Studio, должна быть запрещена. Более того, несовместимый проект не может быть обновлен или исправлен. Таким образом, проект необходимо проверять на совместимость дважды: в первый раз, когда он рассматривается для обновления или исправления, и во второй раз перед его загрузкой.  
  
 Чтобы включить определение несовместимости проекта, необходимо реализовать <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly%2A> и <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A> методы. Если проект несовместим, метод `UpgradeProject_CheckOnly` должен вернуть код подтверждения `VS_S_INCOMPATIBLEPROJECT`, а метод `CreateProject` — код ошибки `VS_E_INCOMPATIBLEPROJECT`. Для версионных проектов необходимо реализовать метод `IVsProjectFlavorUpgradeViaFactory2.UpgradeProjectFlavor_CheckOnly` вместо `IVsProjectUpgradeViaFactory4.UpgradeProject_CheckOnly`.  
  
 Система проектов называется версионной, если помимо основного проекта существует сборка веб-проекта, проекта Office (VSTO), Silverlight или другого типа проекта. Более старые системы проектов, которые уже реализуют `IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly` , и версионные системы проектов, которые уже реализуют `IVsProjectFlavorUpgradeViaFactory.UpgradeProjectFlavor_CheckOnly` , продолжают поддерживаться. Старая версия `IVsProjectUpgradeViaFactory.UpgradeProject_CheckOnly` имеет следующую сигнатуру реализации:  
  
```  
IVsProjectUpgradeViaFactory::UpgradeProject_CheckOnly(  
  
/* [in] */ BSTR bstrFileName,  
/* [in] */ IVsUpgradeLogger *pLogger,  
/* [out] */ BOOL *pUpgradeRequired,  
/* [out] */ GUID *pguidNewProjectFactory,  
/* [out] */ VSPUVF_FLAGS *pUpgradeProjectCapabilityFlags  
)  
```  
  
 Если этот метод устанавливает `pUpgradeRequired` в значение TRUE и возвращает `S_OK`, результат рассматривается как "Обновить", как если бы метод установил для флага обновления значение `VSPUVF_PROJECT_ONEWAYUPGRADE`, которое описывается ниже в этом разделе. Следующие возвращаемые значения поддерживаются с помощью этого старого метода, но только если `pUpgradeRequired` имеет значение TRUE:  
  
1.  `VS_S_PROJECT_SAFEREPAIRREQUIRED`. Это возвращаемое значение преобразует значение `pUpgradeRequired` в TRUE, что эквивалентно значению `VSPUVF_PROJECT_SAFEREPAIR`, которое описывается далее в этом разделе.  
  
2.  `VS_S_PROJECT_UNSAFEREPAIRREQUIRED`. Это возвращаемое значение преобразует значение `pUpgradeRequired` в TRUE, что эквивалентно значению `VSPUVF_PROJECT_UNSAFEREPAIR`, которое описывается далее в этом разделе.  
  
3.  `VS_S_PROJECT_ONEWAYUPGRADEREQUIRED`. Это возвращаемое значение преобразует значение `pUpgradeRequired` в TRUE, что эквивалентно значению `VSPUVF_PROJECT_ONEWAYUPGRADE`, которое описывается далее в этом разделе.  
  
 Новые реализации в `IVsProjectUpgradeViaFactory4` и `IVsProjectFlavorUpgradeViaFactory2` позволяют более точно указывать тип миграции.  
  
> [!NOTE]
>  Вы можете кэшировать результат проверки совместимости с помощью метода `UpgradeProject_CheckOnly` , чтобы этот результат также мог использоваться в последующем вызове метода `CreateProject`.  
  
 Например если `UpgradeProject_CheckOnly` и `CreateProject` методы, предназначенные для [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] с системой проекта с пакетом обновления 1, проверяют файл проекта и обнаруживают, что `<MinimumVisualStudioVersion>` свойство сборки имеет значение «11.0», Visual Studio 2010 с пакетом обновления 1 не будет загружать проект. Кроме того, **навигатор по решению** укажет, что проект "несовместим", и не загрузит его.  
  
##  <a name="BKMK_UpgradeLogger"></a> Обновление средства ведения журнала  
 Вызов `IVsProjectUpgradeViaFactory::UpgradeProject` содержит средство ведения журнала `IVsUpgradeLogger` , которое системы проектов и версии проектов должны использовать, чтобы предоставлять подробную трассировку обновления для устранения неполадок. Если регистрируется предупреждение или ошибка, Visual Studio отображает отчет об обновлении.  
  
 При выполнении записи в средство ведения журнала обновления придерживайтесь следующих рекомендаций.  
  
-   Visual Studio вызовет метод Flush, когда завершится обновление всех проектов. Не вызывайте Flush в своей системе проектов.  
  
-   Функция LogMessage имеет следующие значения ErrorLevel:  
  
    -   0 — для всех сведений, которые требуется отслеживать;  
  
    -   1 — для предупреждения;  
  
    -   2 — для ошибки;  
  
    -   3 — для модуля форматирования отчета. При обновлении проекта зарегистрируйте слово Converted один раз; не локализуйте это слово.  
  
-   Если проекту не требуется никакое исправление или обновление, Visual Studio будет создавать файл журнала только в том случае, если система проектов зарегистрировала предупреждение или ошибку во время выполнения метода UpgradeProject_CheckOnly или UpgradeProjectFlavor_CheckOnly.