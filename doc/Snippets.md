Magento Admin Snippets
======================

System Configuration
--------------------

### Types of List Fields

    * button
    * checkbox
    * checkboxes
    * column
    * date
    * editablemultiselect
    * editor
    * fieldset
    * file
    * gallery
    * hidden
    * image
    * imagefile
    * label
    * link
    * multiline
    * multiselect
    * note
    * obscure
    * password
    * radio
    * radios
    * reset
    * select
    * submit
    * text
    * textarea
    * time

#### Yes/No using a Select Field  ####
```
<field id="enable" translate="label" type="select" 
       sortOrder="1" 
       showInDefault="1" showInWebsite="0" showInStore="0">
    <label>Module Enable</label>
    <source_model>Magento\Config\Model\Config\Source\Yesno</source_model>
    <comment>System Config Enabled Yes/No</comment>
</field>
```


