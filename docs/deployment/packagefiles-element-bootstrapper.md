---
title: '&lt;PackageFiles&gt; элемент (загрузчик) | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <PackageFiles> element [bootstrapper]
ms.assetid: 3ea252d7-18a3-47d8-af83-47feebcfe82b
caps.latest.revision: 16
author: stevehoag
ms.author: shoag
manager: wpickett
ms.workload:
- multiple
ms.openlocfilehash: 25ba72b511782c450b882826a3e3af94a14f6e20
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ltpackagefilesgt-element-bootstrapper"></a>&lt;PackageFiles&gt; элемент (загрузчик)
`PackageFiles` Элемент содержит `PackageFile` элементы, которые определяют установочные пакеты, выполняемые в результате использования `Command` элемента.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<PackageFiles  
    CopyAllPackageFiles  
>  
    <PackageFile   
        Name  
        HomeSite  
        CopyOnBuild  
        PublicKey  
        Hash  
    />  
</PackageFiles>  
```  
  
## <a name="elements-and-attributes"></a>Элементы и атрибуты  
 `PackageFiles` Элемент имеет указанный ниже атрибут.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`CopyAllPackageFiles`|Необязательный. Если значение `false`, программа установки будет загружать только файлы, на которые ссылается `Command` элемента. Если значение `true`, все файлы будут загружены.<br /><br /> Если значение `IfNotHomesite`, программа установки будет функционировать так же, как если бы `False` Если `ComponentsLocation` задано значение `HomeSite`и в противном случае будет функционировать так же, как если бы `True`. Этот параметр можно использовать разрешить пакетам, которые сами являются начальных загрузчиков, сделайте выполнить свою в сценарии HomeSite.<br /><br /> Значение по умолчанию — `true`.|  
  
## <a name="packagefile"></a>PackageFile  
 `PackageFile` Элемент является дочерним элементом `PackageFiles` элемента. Объект `PackageFiles` элемент должен иметь по крайней мере один `PackageFile` элемента.  
  
 `PackageFile`имеет следующие атрибуты.  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|`Name`|Обязательно. Имя файла пакета. Это имя, `Command` элемент будет ссылаться при определении условий для установки пакета. Это значение также используется как ключ в `Strings` таблицы, чтобы получить локализованное имя, средства, такие как [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] будет использовать для описания пакета.|  
|`HomeSite`|Необязательный. Расположение пакета на удаленном сервере, если не включено в установщик.|  
|`CopyOnBuild`|Необязательный. Указывает, является ли начальный загрузчик должен копировать файл пакета на диск во время построения. Значение по умолчанию — true.|  
|`PublicKey`|Зашифрованный открытый ключ заверителя сертификата пакета. Обязателен, если `HomeSite` используется; в противном случае — необязательно.|  
|`Hash`|Необязательный. Хэш SHA1 файла пакета. Используется для проверки целостности файла во время установки. Если идентичный хэш не удается вычислить из файла пакета, пакет не устанавливается.|  
  
## <a name="example"></a>Пример  
 В следующем примере кода определяет пакеты для [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] распространяемый пакет и его зависимостей, таких как установщик Windows.  
  
```  
<PackageFiles>  
    <PackageFile Name="instmsia.exe" HomeSite="InstMsiAExe" PublicKey="3082010A0282010100AA99BD39A81827F42B3D0B4C3F7C772EA7CBB5D18C0DC23A74D793B5E0A04B3F595ECE454F9A7929F149CC1A47EE55C2083E1220F855F2EE5FD3E0CA96BC30DEFE58C82732D08554E8F09110BBF32BBE19E5039B0B861DF3B0398CB8FD0B1D3C7326AC572BCA29A215908215E277A34052038B9DC270BA1FE934F6F335924E5583F8DA30B620DE5706B55A4206DE59CBF2DFA6BD154771192523D2CB6F9B1979DF6A5BF176057929FCC356CA8F440885558ACBC80F464B55CB8C96774A87E8A94106C7FF0DE968576372C36957B443CF323A30DC1BE9D543262A79FE95DB226724C92FD034E3E6FB514986B83CD0255FD6EC9E036187A96840C7F8E203E6CF050203010001"/>  
    <PackageFile Name="WindowsInstaller-KB884016-v2-x86.exe" HomeSite="Msi30Exe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>  
    <PackageFile Name="dotnetfx.exe" HomeSite="DotNetFXExe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>  
    <PackageFile Name="dotnetchk.exe"/>  
</PackageFiles>  
```  
  
## <a name="see-also"></a>См. также  
 [\<Продукта > элемент](../deployment/product-element-bootstrapper.md)   
 [\<Пакет > элемент](../deployment/package-element-bootstrapper.md)   
 [Справочные сведения о схеме пакетов и продуктов](../deployment/product-and-package-schema-reference.md)