Interfaces
==========

Model Interfaces
----------------

.. _component_archetype_model_archetype-interface:

ArchetypeInterface
~~~~~~~~~~~~~~~~~~

This interface should be implemented by models representing an **Archetype**.

.. note::

    This interface extends the :ref:`component_archetype_model_archetype-translation-interface`
    and the :ref:`component_resource_model_timestampable-interface`. |br|
    You will find more information about this interface in `Sylius Api ArchetypeInterface`_.

.. _Sylius Api ArchetypeInterface: http://api.sylius.org/Sylius/Component/Archetype/Model/ArchetypeInterface.html


.. _component_archetype_model_archetype-translation-interface:

ArchetypeTranslationInterface
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

This interface should be implemented by models representing an **ArchetypeTranslation**.

.. note::

    You will find more information about this interface in `Sylius Api ArchetypeTranslationInterface`_.

.. _Sylius Api ArchetypeTranslationInterface: http://api.sylius.org/Sylius/Component/Archetype/Model/ArchetypeTranslationInterface.html


.. _component_archetype_model_archetype-subject-interface:

ArchetypeSubjectInterface
~~~~~~~~~~~~~~~~~~~~~~~~~

To characterize an object with attributes and options from a common archetype,
the object class needs to implement the ``ArchetypeSubjectInterface``.

.. note::

    This interface extends the :ref:`component_attribute_model_attribute-subject-interface`
    and the :ref:`component_variation_model_variable-interface`. |br|
    You will find more information about this interface in `Sylius Api ArchetypeSubjectInterface`_.

.. _Sylius Api ArchetypeSubjectInterface: http://api.sylius.org/Sylius/Component/Archetype/Model/ArchetypeSubjectInterface.html


Services Interfaces
-------------------

.. _component_archetype_builder_archetype-builder-interface:

ArchetypeBuilderInterface
~~~~~~~~~~~~~~~~~~~~~~~~~

This interface should be implemented by services that will build the archetypes of products.

.. note::

    You will find more information about this interface in `Sylius Api ArchetypeBuilderInterface`_.

.. _Sylius Api ArchetypeBuilderInterface: http://api.sylius.org/Sylius/Component/Archetype/Builder/ArchetypeBuilderInterface.html
