# Change Log
All notable changes to this project will be documented in this file.

## [1.10.1] 2018-01-03

### Fixed

- Minor bug fixes.

## [1.10] 2017-12-30

### Fixed
- Remove the ability to print work order documents for an unreleased work order.
- All cookies have flags set based on values from php.ini, e.g. secure, HttpOnly.

### Added
- Click info provides a way of showing additional information to the user in uzERP’s grids without having to click through to the underlying data view. See: https://doc.uzerp.com/Setup/Model-Customisation#model-customisation_click-info.
- Enable tagging of reports.
- Add costs for SO Products that are not linked to a Stock Item, allows margin reporting against non-stocked products.

## Changed
- Useful utility files moved to /utils directory.

## [1.9.1] 2017-11-24

### Fixed
- Posted accrual journals not updating GL balances (regression).
- Correct payment terms belongsTo reference on SInvoice model. Prevents database error when adding display field.
- Show item description when creating invoice from GRN.

## [1.9] 2017-09-04

### Fixed

- Multi Bin Balances Print uzLET now sends a CSRF token with its form data.
- Javascript error when adding a new Periodic Payment.
- Posting supplier journal always fails with 'Cannot post journal to a control account'.
- Use customer currency in aged analysis on statements.

### Added

- Product Management improvements
    - Update linked product and productline descriptions when editing Stock Item or SO/PO Product.
    - Clone sales products and product lines with stock item
- Free-text fields on Company Contact record (text1, text2), for user use.
- Show pickable stock balance when viewing an item

### Changed

- Move Sentry client config into uzERP config file.
- Allow user theme.css to have a suffix for browser cache-busting. e.g. add the date to the filename when changed -- theme-20170727.css.

## [1.8.2] 2017-07-14
### Fixed
- Prevent further GRNs being created for part received purchase orders that have reverted to requisitions.

- Product selector fixes
    - Show all currently linked targets when amending component list
    - Allow scrolling of component list
    - Return to the item being edited after saving links


### Added
- Site specific Works Order document injector classes are loaded from user/classes
- WOOperationsReport injector class, e.g. to produce a route card document with operations (define a report definition with Name = wo_operations). Add the class in Setup > System Admin > Injector Classes, as required.
- Site specific modules can be created in user/modules

### Changed
- Works Order documents can be selected, then printed or viewed
- Works Order documents can be sent to a selected printer

## [1.8.1] 2017-06-08
### Fixed
- Allow gulp to be run using 'npm run gulp'

### Added
- Add jquery.watermark.js, used by autocomplete fields

### Changed
- Replace clear_memcached.php script with flush_memcached.php

## [1.8] 2017-05-27
### Fixed
- Adding a holiday request now uses the correct allocation period.
- Resetting user passwords now sends email notifications.
- Error when cancelling Sales Order product selector actions.
- Prevent users from seeing and acting on expenses of other employees that they are not authorisers for.
- Ensure that a GL transaction cannot be saved to a closed period.
- Prepopulate correct GL Account and Centre combination when displaying the Cashbook transaction refund form.
- Prevent posting of Sales and Purchase Ledger journals to control accounts.
- Prevent posting of invoice templates.
- Replace functions removed in PHP7.

### Added
- Delete action for Sales Order product selectors.

### Changed
- Javascript and less/css is now complied at build time.
    - Use grunt.js to build static assets.
    - Remove /theme and /data/resource_c directories.
    - Remove resource.php and let web server serve static assets.
    - Create /user/theme.css for custom colours, etc.

### Removed
- Manual status change on HR expense actions.

## [1.7.1] 2016-12-13
### Fixed
- Error when saving new CRM activity

## [1.7] - 2016-12-07
### Fixed
- Various Sales Order product selector fixes

### Added
- Print item labels from Sales Order. Requires a Report Definition called 'SOItemLabel'
- Transfer outstanding Sales Order lines to a new order (cancels existing lines)
- View line notes from the Sales Order sidebar
- Show person in Periodic Payments list
- Require confirmation on cancel and authorise Purchase Requisition actions
- A note can be added when setting a Customer Service Failure code
- Custom model sort (see: http://wiki.uzerp.com/doku.php/dev_guide#custom_sort_in_views) allows the default view sorting to be changed.

### Changed
- Security
    - Passwords are hashed using PHP 5.5+ Password hashing API
        - New passwords must now be at least 10 characters long but existing passwords remain unchanged.
        - A password strength meter has been added to encourage password complexity
    - Stronger CSRF protection
- New usernames can only contain lower-case letters and/or numbers.

### Removed
- Unused PHPBarcode library

## [1.6.2] - 2016-05-23
### Fixed
- Error on 'save as new' in sales orders
- Error on 'save as new credit' from sales invoice
- Error on adding a new credit note from customer view
- Sort sales order list when linking purchase order
- Ensure that CRM activity attachments are only listed on their own activity

### Added
- UI to allow deletion of contact notes
- Optional stop controls to prevent creation of sales orders, quotes and templates while a customer account is on stop
- Show note form when placing a customer account on stop

## [1.6.1] - 2016-04-07
### Fixed
- Load correct address when creating new sales order for a person
- Add project_id to SO product views
- Fix product search not returning items when adding sales order lines
- Use concurrency control when updating GL Balances

### Added
- Add customer account number to sales order acknowledgement XML output
- Add customer account and sales order number to purchase order XML output
- Add customer account number to invoice XML output

## [1.6] - 2016-02-16
### Fixed
- Setting a custom theme now uses that theme instead of the default
- Sales order add-line was showing multiple prices for an item
- LDAP login fails if user or system company access disabled
- Prevent Apache FOP errors by encoding less-than '<' as `&#60;` in XML output data

### Added
- Allow Sales Invoices to be allocated to Projects and Tasks
- Works order view from Projects
- Add audit fields to projects
- Add the ability to purchase orders and invoices from a task
- New injector classes for optional LDAP authentication with Apache
- Add a notes field to sales order line input. Not printed on outputs by default
- Purchase orders can be linked to a sales order
- Purchase order delivery address can be sourced from a linked sales order, for output only
- Despatch notes can be created for non-stock product lines
- Products can be marked as 'not despatchable', i.e. their product lines can't be added to despatch notes
- Sales order lines can be released and added to a despatch note for the sales order sidebar
- Purchase order schedule document print
- Site-wide preference to list all purchase orders, instead of only those raised by the logged in user.
- Improvements to CRM Activities
- Statement date and page shown in cashbook transactions view
- Sales orders/quotes list and 'new' action from Person side-bar

### Changed
- Simplify template for getting opportunity details from a project
- Phinx migrations moved to schema/phinx/migrations
- Project Budget Controller to show budgets correctly

### Removed
- Unnecessary action in the Task sidebar removed
- Redundant EGS reports from projects


## [1.5.2] - 2015-05-15
### Fixed
- Report module not working

### Changed
- adodb will be installed from our fork of v5.18 at https://bitbucket.org/uzerp/adodb

## [1.5.1] - 2015-04-09
### Changed
- Make changelog more useful to users - [keepachangelog.com](http://keepachangelog.com/)
- Modify Sales Invoice VAT handling for Prompt Payment Discounts to agree with new UK legislation, [HMRC Brief 49 (2014): VAT - Prompt Payment Discounts](https://www.gov.uk/government/publications/revenue-and-customs-brief-49-2014-vat-prompt-payment-discounts/revenue-and-customs-brief-49-2014-vat-prompt-payment-discounts)
  - Stage 1 - Don't adjust invoice VAT/net, store gross discount

### Added
- Add an option to sales orders to print an address label. You will need to add a permission for controller: SordersController, action: printAddressLabel and create a Report Definition called 'SOAddressLabel'.

## [1.5.0] - 2015-03-20
### Fixed
- View purchase orders/invoices while viewing a PO Product Line

### Changed
- adodb and less-php libraries must now be installed via [composer](https://getcomposer.org/) and not distributed in the *plugins* folder.

## [1.4.0] - 2015-03-10
### Fixed
- A person added without a company link will now be visible in the list of people

### Added
- Controller smarty templates can be overridden by users
- Support for logging to [Sentry](https://getsentry.com/)

### Changed
- The smarty php library must now be installed via [composer](https://getcomposer.org/) and not distributed in the *plugins* folder.

## [1.3.11] - 2015-02-17
### Fixed
- Stop Sales Invoice being created for customers on stop

### Added
- Allow empty sales orders to be cancelled

## [1.3.10] - 2015-01-20
### Fixed
- Closing final period of year fails when trying to update assets

### Added
- Make VAT amounts availabe to Sales Order Acknowledgement print

## [2014.3.9] - 2014-12-01
### Fixed
- Warehouse locations without GL Accounts should be visible
- Empty response when selecting User Space Tables from the menu
- When editing a task the project should not be changed
- Add NOT NULL constraint on project_id column in tasks table

### Added
- Make admin from email address configurable

### Changes to Projects Module
- Changes expenses to link to make task selection dependent on project selection in expenses header
- Add project tasks to purchase order header and make dependent on project. Also fix small annoyance where address heading incorrect on view.
- Add Purchase orders sidebar link on projects
-  Changes to allow projects and tasks in entered purchase invoices

## [2014.3.8] - 2014-10-09
### Fixed
- CSV outputs are empty

### Changes to Projects Module
- Changes to projects module
- Tidy up projects controller:
  - Removed code for old ezPDF 'reports' that no longer work
  - Removed deprecated actions for a project
  - Changed view sidebar actions (added go to and add projects under actions)
- Tidy up the projects entry and display screen:
  - Set project identifier to be job_no+name
  - Remove RAG status from view template (code left in controller as may be useful)
  - Remove edit template as not required
  - Update new template so can be used for edits as well
- Minor changes to template new.tpl
- Update so that a project can be marked as complete and the status is changed to 'C'. Doesn't change any other validations yet.
- Another change to the template to get the fields in the correct order
- Tidy up the Project Task sidebar so in the same basic order as Projects Remove calendar views as they don't currently work
- Change the order of Project Budget Item Type to Materials, Equipment, Resources, Other
- Small change to opportunity search
- Fixed bug re opportunity identifier field not displaying in drop down correctly
- Change to tasks template when adding from a project
- Fixed Bug to limit person dropdown when allocating task hours.
  - When entering task hours person dropdown now only shows people from the system company 
  - Note - this means that 'non employees' can still book hours IF they are in the system company as people.
- Fixed Bug to limit person dropdown when setting up resource templates
- Fixed bug on task hours total in View Task Totals
- Changes to the way project module handles resources
- Fixed bug which allowed hours with no employee also removed overtime checkbox as deprecated
- To add value to opportunities and products plus tidy up lik 'opportunity to project'
- Add database migration for project module updates
								  
## [2014.3.7] - 2014-09-15
### Fixed
- Duplicate NI number should be allowed in combination with finish date in HR - New Employee

## [2014.3.6] - 2014-09-09
### Fixed
- Regression in report definitions
- VAT totals incorrect on Sales Order Quote print
- Error adding periodic payment for Sales/Purchase Ledger Source

### Added
- Show person name on Sales Quote print

## [2014.3.5] - 2014-08-20
### Fixed
- Broken link on view purchase order supply/demand
- Parentheses arround address fields cause SQL error

### Added
- Print company bank account details on pro-forma invoice
- Show customer phone numbers on confirm sale
- Show line due dates on sales order acknowledgement
- Show sales order number on sales invoice

## [2014.3.4] - 2014-07-22
### Fixed
- Remove call by reference outside function definitions for PHP 5 compatibility

## [2014.3.3] - 2014-07-08
### Added
- Open up project job number for editing and enhance the search options

## [2014.3.2] - 2014-06-24
### Added
- Allow selection of a custom XSL report defintion for reports.

## [2014.3.1] - 2014-06-11
### Fixed
- Sales Order Acknowledgement Print, lines overwrite header
- CRM Activities view loads calendar instead of activities
- Adding a project fails due to system policy error
- OS Value on batch payments not being set to zero

### Added
- Use [composer](https://getcomposer.org/) to install PHP libs
- phinx for database migrations

## [2014.3] - 2014-05-27
### Changed
- First Git controlled release on bitbucket
- Older release notes at [uzerp.com](http://www.uzerp.com/releases)


[1.10.1]: https://github.com/uzerpllp/uzerp/compare/1.10...1.10.1
[1.10]: https://github.com/uzerpllp/uzerp/compare/1.9.1...1.10
[1.9.1]: https://github.com/uzerpllp/uzerp/compare/1.9...1.9.1
[1.9]: https://github.com/uzerpllp/uzerp/compare/1.8.2...1.9
[1.8.2]: https://github.com/uzerpllp/uzerp/compare/1.8.1...1.8.2
[1.8.1]: https://github.com/uzerpllp/uzerp/compare/1.8...1.8.1
[1.8]: https://github.com/uzerpllp/uzerp/compare/1.7.1...1.8
[1.7.1]: https://github.com/uzerpllp/uzerp/compare/1.7...1.7.1
[1.7]: https://github.com/uzerpllp/uzerp/compare/1.6.2...1.7
[1.6.2]: https://github.com/uzerpllp/uzerp/compare/1.6.1...1.6.2
[1.6.1]: https://github.com/uzerpllp/uzerp/compare/1.6...1.6.1
[1.6]: https://github.com/uzerpllp/uzerp/compare/1.5.2...1.6
[1.5.2]: https://github.com/uzerpllp/uzerp/compare/1.5.1...1.5.2
[1.5.1]: https://github.com/uzerpllp/uzerp/compare/1.5.0...1.5.1
[1.5.0]: https://github.com/uzerpllp/uzerp/compare/1.4.0...1.5.0
[1.4.0]: https://github.com/uzerpllp/uzerp/compare/1.3.11...1.4.0
[1.3.11]: https://github.com/uzerpllp/uzerp/compare/1.3.10...1.3.11
[1.3.10]: https://github.com/uzerpllp/uzerp/compare/2014.3.9...1.3.10
[2014.3.9]: https://github.com/uzerpllp/uzerp/compare/2014.3.8...2014.3.9
[2014.3.8]: https://github.com/uzerpllp/uzerp/compare/2014.3.7...2014.3.8
[2014.3.7]: https://github.com/uzerpllp/uzerp/compare/2014.3.6...2014.3.7
[2014.3.6]: https://github.com/uzerpllp/uzerp/compare/2014.3.5...2014.3.6
[2014.3.5]: https://github.com/uzerpllp/uzerp/compare/2014.3.4...2014.3.5
[2014.3.4]: https://github.com/uzerpllp/uzerp/compare/2014.3.3...2014.3.4
[2014.3.3]: https://github.com/uzerpllp/uzerp/compare/2014.3.2...2014.3.3
[2014.3.2]: https://github.com/uzerpllp/uzerp/compare/2014.3.1...2014.3.2
[2014.3.1]: https://github.com/uzerpllp/uzerp/compare/2014.3...2014.3.1

