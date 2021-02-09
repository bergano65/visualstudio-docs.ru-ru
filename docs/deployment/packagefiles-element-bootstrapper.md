---
title: '&lt;&gt;Элемент паккажефилес (начальный загрузчик) | Документация Майкрософт'
description: Сведения об элементе Паккажефилес, содержащем элементы PackageFile, которые определяют пакеты установки, выполняемые в результате выполнения элемента Command.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- <PackageFiles> element [bootstrapper]
ms.assetid: 3ea252d7-18a3-47d8-af83-47feebcfe82b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0fbf76fec604819d7944a7b54fa4b2421e37c111
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925363"
---
# <a name="ltpackagefilesgt-element-bootstrapper"></a>&lt;&gt;Элемент паккажефилес (начальный загрузчик)
`PackageFiles`Элемент содержит `PackageFile` элементы, которые определяют пакеты установки, выполняемые в результате `Command` элемента.

## <a name="syntax"></a>Синтаксис

```xml
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
 Элемент `PackageFiles` имеет указанный ниже атрибут.

|Атрибут|Описание|
|---------------|-----------------|
|`CopyAllPackageFiles`|Необязательный элемент. Если задано значение `false` , установщик будет скачивать только файлы, на которые ссылается `Command` элемент. Если задано значение `true` , будут скачаны все файлы.<br /><br /> Если задано значение `IfNotHomesite` , установщик будет вести себя так, как `False` Если `ComponentsLocation` бы параметр был установлен в значение `HomeSite` , а в противном случае будет действовать так же, как если бы `True` . Этот параметр может быть полезен для того, чтобы пакеты, которые сами являются загрузчиками, могли выполнять собственное поведение в сценарии HomeSite.<br /><br /> Значение по умолчанию — `true`.|

## <a name="packagefile"></a>PackageFile
 `PackageFile`Элемент является дочерним по отношению к `PackageFiles` элементу. `PackageFiles`Элемент должен иметь по крайней мере один `PackageFile` элемент.

 `PackageFile` имеет следующие атрибуты.

| Атрибут | Описание |
|---------------| - |
| `Name` | Обязательный элемент. Имя файла пакета. Это имя, `Command` на которое будет ссылаться элемент, когда он определяет условия, при которых пакет устанавливается. Это значение также используется в качестве ключа в `Strings` таблице для получения локализованного имени, которое [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] будет использоваться инструментами для описания пакета. |
| `HomeSite` | Необязательный элемент. Расположение пакета на удаленном сервере, если оно не включено в установщик. |
| `CopyOnBuild` | Необязательный элемент. Указывает, должен ли загрузчик копировать файл пакета на диск во время сборки. Значение по умолчанию — true. |
| `PublicKey` | Зашифрованный открытый ключ для подписи сертификата пакета. Требуется `HomeSite` , если используется. в противном случае — необязательный. |
| `Hash` | Необязательный элемент. Хэш SHA1 файла пакета. Используется для проверки целостности файла во время установки. Если идентичный хэш не может быть вычислен из файла пакета, то пакет не будет установлен. |

## <a name="example"></a>Пример
 В следующем примере кода определяются пакеты для распространяемого пакета платформа .NET Framework и его зависимостей, таких как установщик Windows.

```xml
<PackageFiles>
    <PackageFile Name="instmsia.exe" HomeSite="InstMsiAExe" PublicKey="3082010A0282010100AA99BD39A81827F42B3D0B4C3F7C772EA7CBB5D18C0DC23A74D793B5E0A04B3F595ECE454F9A7929F149CC1A47EE55C2083E1220F855F2EE5FD3E0CA96BC30DEFE58C82732D08554E8F09110BBF32BBE19E5039B0B861DF3B0398CB8FD0B1D3C7326AC572BCA29A215908215E277A34052038B9DC270BA1FE934F6F335924E5583F8DA30B620DE5706B55A4206DE59CBF2DFA6BD154771192523D2CB6F9B1979DF6A5BF176057929FCC356CA8F440885558ACBC80F464B55CB8C96774A87E8A94106C7FF0DE968576372C36957B443CF323A30DC1BE9D543262A79FE95DB226724C92FD034E3E6FB514986B83CD0255FD6EC9E036187A96840C7F8E203E6CF050203010001"/>
    <PackageFile Name="WindowsInstaller-KB884016-v2-x86.exe" HomeSite="Msi30Exe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>
    <PackageFile Name="dotnetfx.exe" HomeSite="DotNetFXExe" PublicKey="3082010A0282010100B22D8709B55CDF5599EB5262E7D3F4E34571A932BF94F20EE90DADFE9DC7046A584E9CA4D1D84441FB647E0F65EEC817DA4DDBD9D650B40C565B6C16884BBF03EE504883EC4F88939A51E394197FFAB397A5CE606D9FDD4C9338BDCD345971E686CEE98399A096B8EAE0445B1342B93A484E5472F70896E400C482017643AF61C2DBFAE5C5F00213DDF835B40F0D5236467443B1A2CA9CDD7E99F1351177FB1526018ECFE0B804782A15FD72C66076910CE74FB218181B6989B4F12F211B66EACA91C7460DB91758715856866523D10232AE64A06FDA5295FDFBDD8D34F5C10C35A347D7E91B6AFA0F45B4E8321D7019BDD1F9E5641FEB8737EA6FD40D838FFD0203010001"/>
    <PackageFile Name="dotnetchk.exe"/>
</PackageFiles>
```

## <a name="see-also"></a>См. также раздел
- [Элемент \<Product>](../deployment/product-element-bootstrapper.md)
- [Элемент \<Package>](../deployment/package-element-bootstrapper.md)
- [Справочник по схеме продуктов и пакетов](../deployment/product-and-package-schema-reference.md)