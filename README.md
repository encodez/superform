# Superform
Simple way to create and validate Phalcon 2 form inpired by the laravel request

### Please fork this repository and help improve.

The module is in development stage. This is a quick reference. Still the module and documentation has to be improved. I will be adding more notes as I get time

example:

```
use Encodez\Superform\Form;
class ClientForm extends Form
{
    public function __construct()
    {
        $this->setMethod(Form::METHOD_POST);
        parent::__construct();
    }

    function getFields()
    {
        return [
            'client_name' => [ 'text', 'Client Name', 'class:form-control'],
            'email' => ['email', 'EMail', 'class:form-control'],
            'building_no' => ['numeric', 'Building No', 'class:form-control'],
            'location_name' => [ 'text', 'Location Name', 'class:form-control location'],
        ];
    }

    function getRules()
    {
        return [
            'client_name' => 'required|length:5,10',
            'building_no' => 'required',
            'email' => 'required|email',
            'location_name' => 'required',
        ];
    }

    /* TODO: Add sanitizers*/
    function getFilters()
    {
        return [
            'client_name' => 'trim'
        ];
    }

    function getCustomMessages()
    {
        return [
            'client_name:required' => 'Client name is required',
            'client_name:length:5,10' => 'Client name must be atleast 5 characters and must not exceed 10',
            'client_name:string' => 'Client name contains invalid characters',
        ];
    }
}
```
