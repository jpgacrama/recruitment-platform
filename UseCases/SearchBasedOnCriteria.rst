.. _SearchBasedOnCriteria:

UC: Search Candidates based on Criteria
=================================================================================================================================

``SearchBasedOnCriteria``

Triggers:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

    User wants to know which candidates match his/her search string

Pre-conditions:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

    None

Description:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. uml::

    @startuml

        actor "Recruiter" as Recruiter
        participant "UI" as UI
        participant "Search Engine" as SearchEngine
        participant "Database" as Database

        Recruiter  -> UI: Enter Search String
        UI -> SearchEngine: Pass Search String to Search Engine
        SearchEngine -> Database: Perform queries to Database

        alt No Results Returned
            Database -> SearchEngine: No results returned
        else
            Database -> SearchEngine: Return Search Results
        end

        alt No Results Returned
            SearchEngine -> UI: Display message that nothing matches your criteria
        else
            SearchEngine -> UI: Display Search Results
        end

    @enduml

Post-conditions:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

    User profile is saved to the database.

Exceptions:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

    None

Notes and Issues:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

    None

References to High-Level Requirements:
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

    - :ref:`ExactMatchSearch`
    - :ref:`ExcludeOperatorInSearchString`
    - :ref:`LogicalAndSearch`
    - :ref:`LogicalOrSearch`
    - :ref:`SearchEngineDefaultFunctionality`

