---
title: Entités de caractères XML et XAML
ms.date: 03/30/2017
f1_keywords:
- '&'
- '&amp'
- '&gt'
- '&lt'
helpviewer_keywords:
- XAML [XAML Services], special characters
- ampersand (&) [XAML Services]
- special characters [XAML Services]
- apostrophe (') [XAML Services]
- greater-than (>) character [XAML Services]
- XAML [XAML Services], quotation mark (")
- XAML [XAML Services], apostrophe (')
- '& (ampersand) [XAML Services]'
- XAML [XAML Services], & (ampersand)
- XAML [XAML Services], escape sequence
- quotation mark (") [XAML Services]
- less-than (<) character [XAML Services]
ms.assetid: 6896d0ce-74f7-420a-9ab4-de9bbf390e8d
ms.openlocfilehash: b4621da21200e6c9e2b174a0e2ba508a4f6bab92
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938708"
---
# <a name="xml-character-entities-and-xaml"></a>Entités de caractères XML et XAML
XAML utilise des entités de caractères définies en XML pour les caractères spéciaux. Cette rubrique décrit des entités de caractères spécifiques et les considérations générales pour d'autres concepts XML en XAML.  
  
<a name="character_entities_and_escaping_issues_that_are_unique_to_xaml"></a>   
## <a name="character-entities-and-escaping-issues-that-are-unique-to-xaml"></a>Entités de caractères et problèmes d'échappement propres à XAML  
 Le balisage XAML utilise généralement les mêmes entités de caractères et séquences d'échappement que celles définies en XML.  
  
 La principale exception réside dans le fait que les accolades ({ et }) ont de l'importance en XAML car ces caractères informent un processeur XAML qu'une séquence de caractères comprise entre les accolades doit être interprétée comme une extension du balisage. Pour plus d’informations sur les extensions de balisage, consultez [Markup Extensions for XAML Overview](markup-extensions-for-xaml-overview.md).  
  
 Toutefois, vous pouvez toujours afficher les accolades comme des caractères littéraux en utilisant une séquence d'échappement propre à XAML plutôt qu'à XML. Pour plus d’informations, consultez [{} séquence d’échappement - Extension de balisage](escape-sequence-markup-extension.md).  
  
 Notez qu’une barre oblique inverse (\\) ne nécessite pas une séquence d’échappement lorsqu’elle est traitée en tant que chaîne.  
  
<a name="xml_character_entities"></a>   
## <a name="xml-character-entities"></a>Entités de caractères XML  
 Comme indiqué précédemment, la plupart des entités de caractères et des séquences d'échappement qui sont généralement utilisées pour écrire le balisage XAML sont définies par XML. Cette rubrique ne présente pas l'intégralité de ces entités ; vous trouverez de nombreuses autres références détaillées des entités dans la documentation externe, par exemple les spécifications XML. Toutefois, pour plus de commodité, cette rubrique présente certaines des entités de caractères XML spécifiques qui sont généralement utilisées dans le balisage XAML.  
  
|Caractère|Entité|Notes|  
|---------------|------------|-----------|  
|& (esperluette)|\&amp;|Doit être utilisé à la fois pour les valeurs d'attribut et pour le contenu d'un élément.|  
|> (supérieur-que le caractère)|\&gt;|Doit être utilisé pour une valeur d’attribut, mais > est acceptable comme contenu d’un élément en tant que < ne le précède pas.|  
|< (moins-que le caractère)|\&lt;|Doit être utilisé pour une valeur d’attribut, mais \< est acceptable comme contenu d’un élément en tant que > ne la respecte pas.|  
|" (guillemets droits)|\&quot;|Doit être utilisé pour une valeur d'attribut, mais le guillemet droit (") est acceptable comme contenu d'un élément. Notez que les valeurs d'attributs peuvent être placées entre un guillemet droit unique (') ou des guillemets droit (") ; le caractère qui apparaît en premier définit ce qui est inclus dans la valeur d'attribut, et l'autre guillemet peut ensuite être utilisé comme littéral dans la valeur.|  
|' (guillemet droit unique)|\&apos;|Doit être utilisé pour une valeur d'attribut, mais le guillemet droit unique (') est acceptable comme contenu d'un élément. Notez que les valeurs d'attributs peuvent être placées entre un guillemet droit unique (') ou des guillemets droit (") ; le caractère qui apparaît en premier définit ce qui est inclus dans la valeur d'attribut, et l'autre guillemet peut ensuite être utilisé comme littéral dans la valeur.|  
|(mappages de caractères numériques)|&#*[integer]*; or &#x *[hex]*;|XAML prend en charge les mappages de caractères numériques dans de l'encodage actif.|  
|(espace insécable)|&\#160 ; (en supposant que le codage UTF-8)|Pour les éléments de document dynamique ou les éléments qui acceptent du texte tels que le <xref:System.Windows.Controls.TextBox> WPF, les espaces insécables ne sont pas normalisés hors du balisage, même pour `xml:space="default"`. (Pour plus d’informations, consultez [blancs en XAML traitement](whitespace-processing-in-xaml.md).)|  
  
<a name="xml_comment_format"></a>   
## <a name="xml-comment-format"></a>Format de commentaire XML  
 XAML utilise le format de commentaire XML : le début du commentaire est `<!--`, la fin du commentaire est `-->,` et la séquence `--` ne doit pas se produire dans un commentaire.  
  
<a name="xml_processing_instructions"></a>   
## <a name="xml-processing-instructions"></a>Instructions de traitement XML  
 XAML gère les instructions de traitement XML conformément aux spécifications XML, qui déclarent que les instructions doivent être transmises. XAML de traitement dans les Services XAML .NET Framework n’utilise pas les instructions de traitement. Les autres infrastructures existantes qui utilisent XAML n'utilisent pas non plus d'instructions de traitement de XAML.  
  
## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble du langage XAML (WPF)](../wpf/advanced/xaml-overview-wpf.md)
- [Extensions de balisage et XAML WPF](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
- [XamlName, grammaire](xamlname-grammar.md)
- [Espace blanc dans XAML de traitement](whitespace-processing-in-xaml.md)
